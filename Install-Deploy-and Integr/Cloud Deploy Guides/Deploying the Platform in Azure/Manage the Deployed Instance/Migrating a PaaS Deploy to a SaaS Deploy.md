# Migrating a PaaS Deployment to a SaaS Deployment

An existing PaaS or IaaS deployment can be migrated to a ProfiseeCloud SaaS instance as long as you have a valid SQL Server BACPAC file. This process is handled primarily by Profisee staff and can migrate large data sets of over 1,000,000 records, which may take several hours to finish processing. Ensure you set aside sufficient time for the migration to complete.

This process completely replaces any data in the SaaS instance with no opportunity for recovery.

To migrate your deployment:

1. Create a SQL Server BACPAC file that contains your migrated instance using the instructions below in the section "Creating a BACPAC file for your deployment."

If the source deployment is a different version of Profisee than the target instance, the instance will inherit the version of the migrated deployment. To prevent migrating to a downgraded version of Profisee, either upgrade the source instance before generating the BACPAC file, or upgrade the SaaS instance to your desired version after restoring the database.

**Profisee versions older than version *2022.R2* are not supported.**

2. Create a storage account in your Azure cloud to store the BACPAC file, and upload the BACPAC file to the storage account.
3. Provide the access key to this storage account to your Profisee support representative, who will configure your ProfiseeCloud SaaS instance.
4. Once Profisee has confirmed that your instance is available, you may begin operating your ProfiseeCloud SaaS instance.

All solution changes (such as models and strategies) should be deployed to the target instance **after** the instance is confirmed to be available by Profisee.

Due to the instance's authentication configuration and our internal policies, Profisee is not able to log into the application to deploy these objects. These updated artifacts must be deployed by the client

## Creating a BACPAC File for your Deployment

Before migrating your database, your deployment, you will need to create a BACPAC that contains your instance.

1. Before creating the bacpac file, perform the following on the existing database

1. Backup the database in preparation for the following changes
2. Delete the Profisee service account users from the database
3. Optionally remove the on-prem Profisee instance. This will clear the meta.tsystemcluster records. If you do not remove the instance you can update the cluster records after migration as described below.
4. Run the script below to Turn off the Temporal table relationships and delete the history views. Note that this preserves the history record, just removes the relationship between the data and hist tables and deletes the history view. These will be created after the new database is created.
2. Migrate the database using SQL Management Studio (SMS) either by deploying the database to Azure SQL directly or by Exporting the Data Tier Application to create a .bacpac file and use that file to import in Azure SQL to create the database. Before migration delete the current, unneeded Profisee database created during your AKS deployment and reuse that name when migrating your on-prem database into Azure SQL.
3. If you migrated the database without first removing the Profisee instance, you will need to update the meta.tsystemcluster table to change the ServerName to 'profisee-0'. Note if you have multiple nodes, you will update each record with the appropriate profisee pod name (i.e. profisee-0, profisee-1)

These steps are described below in more detail along with the scripts to run.

The following are the considerations and steps required to migrate a Profisee on-prem SQL database to Azure SQL for use in an AKS container.

1. Make a backup of the existing database since the steps below will make the database unusable in the current Profisee instance. Or you can backup and restore the database to create a new database and perform the steps below on the newly created database
2. In SSMS, delete the Profisee service accounts Users from the Profisee database. For example, in this database there are 2 Profisee service accounts corp\svc\_maestro and corp\svc\_web that must be deleted.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i90d93cb87d46107b.png)

3. Delete the existing records in the meta.tSystemCluster table. These records will be cleared when the Profisee instance is removed or you can manually delete the records. If you do not remove the instance you can update the cluster records after migration as described below.
4. Before creating the bacpac file, run the following script which will turn off the Temporal tables and will also delete the History views.

```
-- Turn Off Temporal Tables and Delete History Views

PRINT N'Turning off temporal tables and Dropping history views...';



-- Define the table variable with the correct columns

DECLARE @tblEntities TABLE(

RowNumber INT IDENTITY (1, 1) PRIMARY KEY CLUSTERED NOT NULL,

[Name] VARCHAR(300) NOT NULL,

[Schema] VARCHAR(200) NOT NULL,

[History] VARCHAR(300) NOT NULL);



-- Insert data into the table variable

INSERT INTO @tblEntities ([Name], [Schema], [History])

SELECT

RIGHT(LEFT(t.name, LEN(t.name)-8),LEN(t.name)-9) as [Name]

,s.name AS [Schema]

,RIGHT(t.name, LEN(t.name)-1) AS [History]

FROM

sys.tables t --ON e.[Name] = RIGHT(t.name, LEN(t.name) - 1) -- Adjust this join condition as needed

JOIN

sys.schemas s ON t.schema_id = s.schema_id

WHERE

t.name like '%[_]History';



-- Declare variables for the loop

DECLARE @maxIndex INT,

@currentIndex INT = 1,

@entityId INT,

@entityName VARCHAR(200),

@entitySchema VARCHAR(200),

@entityHistoryName VARCHAR(200),

@versioningOff VARCHAR(MAX),

@removePeriod VARCHAR(MAX),

@dropHistoryView VARCHAR(MAX);



-- Get the maximum index

SELECT @maxIndex = COUNT(*) FROM @tblEntities;



-- Loop through the table variable

WHILE @currentIndex <= @maxIndex

BEGIN

-- Retrieve the current row's data

SELECT @entityName = [Name],

@entitySchema = [Schema],

@entityHistoryName = [History]

FROM @tblEntities

WHERE [RowNumber] = @currentIndex;



-- Construct the SQL statements

SELECT @versioningOff = CONCAT('ALTER TABLE [', @entitySchema, '].[t', @entityName, '] SET (SYSTEM_VERSIONING = OFF)'),

@removePeriod = CONCAT('ALTER TABLE [', @entitySchema, '].[t', @entityName, '] DROP PERIOD FOR SYSTEM_TIME'),

@dropHistoryView = CONCAT('DROP VIEW [', @entitySchema, '].[v', @entityHistoryName, ']');



-- Execute the SQL statements

EXEC(@versioningOff);

EXEC(@removePeriod);

EXEC(@dropHistoryView);



-- Increment the loop index

SET @currentIndex += 1;

END

GO
```

5. To migrate the database, there are 2 options in SSMS, you can deploy the database directly to Azure to create a new database or created a .bacpac file that can be imported into Azure SQL to create the database.
6. To deploy the database directly, in SSMS, right click on the Profisee database and select Tasks -Deploy Database to Microsoft Azure SQL Database. You will then be prompted to select the target Azure SQL Server and specify the name of the database.
7. Alternately you can Export the database to create a .bacpac file. Then Import using that file in Azure SQL to create the database.

In SSMS, right click on the database and select Tasks-Export Data-tier Application. You will then be prompted to specify the name and location of a .bacpac file

After the .bacpac file has been created, connect to your Azure SQL Server instance in SSMS and select to Import the file to create the database in Azure.

In SSMS, connected to your Azure SQL instance and right click on Databases and select Import Data-tier Application.

8. If you migrated the database without first removing the Profisee instance, you should delete the records from the meta.tsystemcluster table that is referencing the original Profisee instance

9. Run the script below to turn on temporal tables.

```
PRINT N'Turning on temporal tables...';



-- Define the table variable with the correct columns

DECLARE @tblEntities TABLE(

RowNumber INT IDENTITY (1, 1) PRIMARY KEY CLUSTERED NOT NULL,

[Name] VARCHAR(300) NOT NULL,

[Schema] VARCHAR(200) NOT NULL,

[History] VARCHAR(300) NOT NULL);



-- Insert data into the table variable

INSERT INTO @tblEntities ([Name], [Schema], [History])

SELECT

RIGHT(LEFT(t.name, LEN(t.name)-8),LEN(t.name)-9) as [Name]

,s.name AS [Schema]

,RIGHT(t.name, LEN(t.name)-1) AS [History]

FROM

sys.tables t --ON e.[Name] = RIGHT(t.name, LEN(t.name) - 1) -- Adjust this join condition as needed

JOIN

sys.schemas s ON t.schema_id = s.schema_id

WHERE

t.name like '%[_]History';



-- Declare variables for the loop

DECLARE @maxIndex INT,

@currentIndex INT = 1,

@entityName VARCHAR(200),

@entitySchema VARCHAR(200),

@entityHistoryName VARCHAR(200),

@addPeriod VARCHAR(MAX),

@versioningOn VARCHAR(MAX),

@createHistoryView VARCHAR(MAX);



-- Get the maximum index

SELECT @maxIndex = COUNT(*) FROM @tblEntities;



-- Loop through the table variable

WHILE @currentIndex <= @maxIndex

BEGIN

-- Retrieve the current row's data

SELECT @entityName = [Name],

@entitySchema = [Schema],

@entityHistoryName = [History]

FROM @tblEntities

WHERE [RowNumber] = @currentIndex;



-- Construct the SQL statements

SELECT @addPeriod = CONCAT('ALTER TABLE [', @entitySchema, '].[t', @entityName, '] ADD PERIOD FOR SYSTEM_TIME ([$ValidFromDTM], [$ValidToDTM])');

IF (@entitySchema = 'data')

BEGIN

SELECT @versioningOn = CONCAT('ALTER TABLE [', @entitySchema, '].[t', @entityName, '] SET (SYSTEM_VERSIONING = ON (HISTORY_TABLE = [', @entitySchema, '].[t', @entityHistoryName, '], HISTORY_RETENTION_PERIOD = 3650 DAYS))');

END

ELSE

BEGIN

SELECT @versioningOn = CONCAT('ALTER TABLE [', @entitySchema, '].[t', @entityName, '] SET (SYSTEM_VERSIONING = ON (HISTORY_TABLE = [', @entitySchema, '].[t', @entityHistoryName, '], HISTORY_RETENTION_PERIOD = 90 DAYS))');

END



-- Execute the SQL statements

EXEC(@addPeriod);

EXEC(@versioningOn);



-- Increment the loop index

SET @currentIndex += 1;

END

GO
```

10. Run the following script to recreate the History views:

```
PRINT N'Recreating the History Views ...';

-- Define the table variable with the correct columns

Create Table #tblEntities (

RowNumber INT IDENTITY (1, 1) PRIMARY KEY CLUSTERED NOT NULL,

Name VARCHAR(300) NOT NULL,

[$UID] uniqueidentifier NOT NULL,

[SchemaName] VARCHAR(200));



--Create History Views

CREATE TABLE #tblAttributes (

RowNumber INT IDENTITY (1, 1) PRIMARY KEY CLUSTERED NOT NULL

,Name VARCHAR(300) NOT NULL

,[ID] INT NOT NULL

,DomainEntityUid NVARCHAR(36));

-- Temporary table to hold schema and table information

DECLARE @schemaTable TABLE (

SchemaName VARCHAR(200),

TableName VARCHAR(300));



DECLARE @maxIndex INT

, @currentIndex INT = 1

, @entityName VARCHAR(50)

, @entityUid uniqueidentifier

, @schema VARCHAR(200)

, @attributeColumns VARCHAR(MAX) = ''

, @attributeIndex INT = 1

, @attributeId INT

, @attributeName VARCHAR(200)

, @maxAttributeIndex INT = 0

, @domainEntityUid NVARCHAR(36)

, @domainEntityName VARCHAR(200)

, @businessRules VARCHAR(MAX) = ''

, @validationStatus VARCHAR(200) = ''

, @joins VARCHAR(MAX) = ''

, @createHistoryView VARCHAR(MAX);

-- Insert all schemas with a t$Entity table into the temporary table

INSERT INTO @schemaTable (SchemaName, TableName)

SELECT

s.name AS SchemaName,

t.name AS TableName

FROM

sys.schemas s

JOIN

sys.tables t ON t.schema_id = s.schema_id

WHERE

t.name = 't$Entity';

-- Declare variables for dynamic SQL

DECLARE @schemaName VARCHAR(200);

DECLARE @entitySql NVARCHAR(MAX);

DECLARE @sql NVARCHAR(MAX);

DECLARE @attributeSql NVARCHAR(MAX);

-- Cursor to iterate over each schema

DECLARE schema_cursor CURSOR FOR

SELECT SchemaName

FROM @schemaTable;

OPEN schema_cursor;

FETCH NEXT FROM schema_cursor INTO @schemaName;

WHILE @@FETCH_STATUS = 0

BEGIN

-- Construct dynamic SQL to insert data from each schema's t$Entity table

SET @entitySql = N'

INSERT INTO #tblEntities

SELECT [Name], [$UID], '''+ @schemaName +'''

FROM ' + QUOTENAME(@schemaName) + '.[t$Entity];';



set @attributeSql = N'

INSERT INTO #tblAttributes

SELECT [Name], [ID], [DomainEntityUid]

FROM ' + QUOTENAME(@schemaName) + '.[t$Attribute] a

WHERE a.[EntityUiD] = @entityUid;;';

EXEC sp_executesql @entitySql;

SELECT @maxIndex = COUNT(*) FROM #tblEntities;

WHILE @currentIndex <= @maxIndex

BEGIN

SELECT @entityName = [Name], @entityUid = [$UID], @schema = [SchemaName] From #tblEntities

WHERE [RowNumber] = @currentIndex;



EXEC sp_executesql @attributeSql, N'@entityUid UNIQUEIDENTIFIER', @entityUid;

SELECT @maxAttributeIndex = COUNT(*) FROM #tblAttributes;

WHILE @attributeIndex <= @maxAttributeIndex

BEGIN

SELECT @attributeName = [Name], @attributeId = [ID], @domainEntityUid = [DomainEntityUid] FROM #tblAttributes

WHERE [RowNumber] = @attributeIndex;



IF @attributeName = 'Name' OR @attributeName = 'Code'

BEGIN

SET @attributeIndex += 1;

CONTINUE;

END

IF @domainEntityUid IS NULL

BEGIN

SET @attributeColumns += CONCAT(',T.[',@attributeName,']');

END

ELSE



BEGIN

SELECT @domainEntityName = Name FROM #tblEntities WHERE [$UID] = @domainEntityUid;

SET @attributeColumns += CONCAT(',[',@attributeName,'].[Code] as [',@attributeName,']');

SET @attributeColumns += CONCAT(',[',@attributeName,'].[Name] as [',@attributeName,'.Name]');

SET @attributeColumns += CONCAT(',[',@attributeName,'].[ID] as [',@attributeName,'.ID]');

SET @joins += CONCAT('LEFT JOIN [',@schema,'].[t',@domainEntityName,'] FOR SYSTEM_TIME ALL [',@attributeName,'] ON [',@attributeName,'].ID = T.[',@attributeName,'] AND txn.EnterDTM > [',@attributeName,'].[$ValidFromDTM] AND txn.EnterDTM <= [',@attributeName,'].[$ValidToDTM]', CHAR(13))

END

SET @attributeIndex += 1;

END



BEGIN

SET @validationStatus = '1 AS ValidationStatusID'

END

SELECT @createHistoryView = CONCAT('CREATE VIEW [',@schema,'].[v', @entityName, '_History] AS

SELECT

T.[ID] as ID

,T.[$UID] as [$UID]

,1 as [$ValidationStatusID]

,T.[Name]

,T.[Code]

,T.[$RecordAvatar]

,T.[$ValidFromDTM]

,T.[$ValidToDTM]

,txn.ID as [$LastChgDataTransactionID]

,T.[$LastChgTypeID]

,T.[$EnterDTM]

,T.[$EnterUserID]

,txn.EnterDTM as [$LastChgDTM]

,T.[$LastChgUserID]

',@attributeColumns,'

',@businessRules,'

FROM

[',@schema,'].[t', @entityName ,'] FOR SYSTEM_TIME ALL T

INNER join [',@schema,'].[t$DataTransaction] txn ON txn.ID = T.[$LastChgDataTransactionID]

', @joins ,'

');

EXEC(@createHistoryView);



SET @attributeColumns = '';

SET @joins = '';

SET @businessRules = '';

SET @currentIndex += 1;

END



select @currentIndex = 1;

DBCC CHECKIDENT (#tblAttributes, RESEED, 1) WITH NO_INFOMSGS;

TRUNCATE TABLE #tblAttributes;

TRUNCATE TABLE #tblEntities;



SET @attributeIndex = 1;



FETCH NEXT FROM schema_cursor INTO @schemaName;

END;

CLOSE schema_cursor;

DEALLOCATE schema_cursor;

DROP TABLE #tblAttributes;

Drop TABLE #tblEntities;
```
11. If running Profisee in an Azure AKS cluster, delete the profisee-0 pod in the AKS cluster which will recreate the pod and will reconfigure the pod to use the new database.

### Additional notes

- All workflows developed before ~23R1 have to be refactored against the newer libraries. This does not constitute a lot of work, but you must have the source code in the old version and then replicate it visually into the new version (against the newer WWF library). Essentially, you must have two Visual Studio setups and do it manually.
- All configuration that goes directly to the DB or STG tables on non-SaaS instances has to be reworked to use the REST API instead of going direct to the Database (SaaS means no table access and no staging tables).
- Any custom subscribers or use of the Profisee SDK must also be refactored/reworked to either use the REST API (preferred) or use the newer version of the SDK (which has to be run in the customer tenant as it cannot be hosted on SaaS).
- When moving from older Profisee versions to SaaS, customers must perform two Profisee upgrades to run a DB script provided by Profisee to upgrade the Profisee history tables to run on SQL Server temporal tables. Without this interim step, customers cannot go straight to the latest Profisee version unless they want to completely dump all of their history in the process.