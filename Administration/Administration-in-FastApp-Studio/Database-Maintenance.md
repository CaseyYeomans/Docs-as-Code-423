# Database Maintenance

## Overview

The Database Maintenance feature automatically performs index rebuilding and statistics updates on the Profisee database according to a configurable schedule. This helps maintain optimal database performance by reducing fragmentation and keeping statistics current.

The configured schedule is based on the Profisee Server's time zone.

By default, the Database Maintenance feature is turned on and scheduled to run every Sunday at 3:00 AM.

**Database Maintenance Schedule for SaaS Customers**

For SaaS environments, the Profisee server time zone is fixed to **UTC**. The default Database Maintenance schedule therefore runs every Sunday at **3:00 AM UTC**.

If you prefer maintenance to occur at a different local time, update the **Database maintenance CRON expression** system setting (under Housekeeping) with a CRON schedule adjusted for the UTC offset of your desired time zone.

For example: To run at 3:00 AM Eastern Time (ET), account for the UTC offset (typically UTC-4 or UTC-5 depending on DST) and convert the desired local time to the equivalent UTC time when defining the CRON expression.

## Controlling Database Maintenance

### Turning it On

Database Maintenance can be turned on only by all of the following:

* Setting the "Database maintenance" system setting under "Housekeeping" to "True"
* Setting the "Database maintenance CRON expression" system setting under "Housekeeping" to a valid CRON expression.

### Turning it Off

Database Maintenance can be turned off by any of the following:

* Setting the **Database maintenance** system setting under **Housekeeping** to **False**.
* Setting the **Database maintenance CRON expression** system setting under **Housekeeping** to a blank value.

### Setting the Schedule

Database Maintenance's schedule can be configured by setting the **Database maintenance CRON expression** system setting under **Housekeeping** to a valid CRON expression.

## Technical Details

### Maintenance Operations

When the maintenance job runs successfully, it performs the following operations:

#### 1. Index Rebuilding

Identifies indexes with:

* Fragmentation ≥ 30%
* Page count ≥ 1,000
* Index type is not HEAP
* Table is not in the exclusion list (`tGlobalPortalApplicationConfiguration`, `tPortalApplicationIcon`)

Rebuilds each qualified index with:

* `ONLINE = ON` (allows concurrent access)
* `MAXDOP = 4` (parallelism limit)
* `FILLFACTOR = 80`

#### 2. Statistics Updates

Updates statistics for all tables except:

* `tGlobalPortalApplicationConfiguration`
* `tPortalApplicationIcon`

Uses `MAXDOP = 4` for parallel processing.

### Hangfire

* The Database Maintenance feature is implemented as a recurring job within Hangfire.
* When Database Maintenance is turned on, an entry with the `Id` of `RunDatabaseMaintenance` will exist at `/api/data/hangfire/recurring`.
* When Database Maintenance is turned off, an entry with the `Id` of `RunDatabaseMaintenance` will not exist at `/api/data/hangfire/recurring`.

### System Settings

#### Database Maintenance Is Enabled

**Setting Name:** `DATABASEMAINTENANCEISENABLED`  
**Display Name:** Database maintenance  
**Description:** Runs database maintenance automatically as scheduled by the database maintenance schedule.

* `False` = Off (do not run)
* `True` = On (do run)

**Data Type:** Boolean

#### Database Maintenance Schedule

**Setting Name:** `DATABASEMAINTENANCECRONEXPRESSION`  
**Display Name:** Database maintenance schedule  
**Description:** Specifies when automated database maintenance runs, using a CRON expression interpreted in the Profisee Server's time zone.

* Empty = Off (maintenance disabled)
* Valid CRON expression = Schedule for when maintenance runs

**Data Type:** Text

### Full SQL Query

Below is the full SQL query executed by Database Maintenance:

```
-- Variables for the WHILE loops
DECLARE @currentID INT
DECLARE @maxID INT

-- Variables for SQL execution
DECLARE @tableName NVARCHAR(512)
DECLARE @indexName NVARCHAR(512)
DECLARE @sql NVARCHAR(MAX)
DECLARE @fillFactor INT = 80

SET NOCOUNT ON;

-- Create temp table to hold the list of indexes
CREATE TABLE #Indexes (
    ID INT IDENTITY(1,1),
    TableName NVARCHAR(512),
    IndexName NVARCHAR(512)
)

-- Populate the temp table with the qualified table names (in order)
INSERT INTO #Indexes (TableName, IndexName)
SELECT 
    QUOTENAME(SCHEMA_NAME(t.[schema_id])) + '.' + QUOTENAME(t.[name]) as tableName,
    QUOTENAME(i.[name]) as indexName
FROM sys.dm_db_index_physical_stats(DB_ID(), NULL, NULL, NULL, 'LIMITED') ips
INNER JOIN sys.tables t ON ips.[object_id] = t.[object_id]
INNER JOIN sys.indexes i ON ips.index_id = i.index_id AND ips.[object_id] = i.[object_id]
WHERE
    t.[name] NOT IN ('tGlobalPortalApplicationConfiguration', 'tPortalApplicationIcon') 
    AND ips.avg_fragmentation_in_percent >= 30.0
    AND ips.page_count >= 1000
    AND ips.index_type_desc != 'HEAP'
ORDER BY tableName;

-- Rebuild indexes (allow multiple indexes per table)
SET @currentID = 1
SELECT @maxID = MAX(ID) FROM #Indexes

WHILE @currentID <= @maxID
BEGIN
    SELECT 
        @tableName = TableName,
        @indexName = IndexName
    FROM #Indexes
    WHERE ID = @currentID

    IF @indexName IS NOT NULL
    BEGIN
        SET @sql = 'ALTER INDEX ' + @indexName + ' ON ' + @tableName + ' REBUILD WITH (ONLINE = ON, MAXDOP = 4, FILLFACTOR = ' + CAST(@fillFactor AS VARCHAR(3)) + ')'
        PRINT @sql
        EXEC sp_executesql @sql
    END

    SET @currentID += 1
END

-- Clean up index rebuild artifacts
DROP TABLE #Indexes

-- Create temp table to hold the list of tables
CREATE TABLE #Tables (
    ID INT IDENTITY(1,1),
    TableName NVARCHAR(512)
)

-- Populate the temp table with the qualified table names (in order)
INSERT INTO #Tables (TableName)
SELECT 
    QUOTENAME(SCHEMA_NAME(t.[schema_id])) + '.' + QUOTENAME(t.[name]) as tableName
FROM sys.tables t
WHERE
    t.[name] NOT IN ('tGlobalPortalApplicationConfiguration', 'tPortalApplicationIcon') 
ORDER BY tableName;

-- Rebuild statistics (once per table)
SET @currentID = 1
SELECT @maxID = MAX(ID) FROM #Tables

WHILE @currentID <= @maxID
BEGIN
    SELECT
        @tableName = TableName
    FROM #Tables
    WHERE ID = @currentID

    IF @tableName IS NOT NULL
    BEGIN
        SET @sql = 'UPDATE STATISTICS ' + @tableName + ' WITH MAXDOP = 4'
        PRINT @sql
        EXEC sp_executesql @sql
    END

    SET @currentID += 1
END

-- Clean up statistic rebuild artifacts
DROP TABLE #Tables
```

---