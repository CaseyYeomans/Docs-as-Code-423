# PaaS Resource Management and Database Management

As PaaS infrastructure is hosted and managed by the client, PaaS infrastructure maintenance is the client's responsibility. Profisee lacks visibility, access, and deep understanding of the customer's infrastructure and may be ill suited to provide advice. Profisee recommends the Kubernetes Administration resource expertise. The following resources are available for client's beginning Azure PaaS implementations:

| | |
| --- | --- |
| AKS Training | [Kubernetes Learning Path (azureedge.net)](https://azurecomcdn.azureedge.net/cvt-c34ccccd7cb5206901b89da17cc492321c45c56283a8d6c1768098aef9936897/mediahandler/files/resourcefiles/kubernetes-learning-path/Kubernetes Learning Path_Version 2.0.pdf/) |
| AZ-900 Azure Fundamentals | [Microsoft Certified: Azure Fundamentals - Learn | Microsoft Docs](https://docs.microsoft.com/en-us/learn/certifications/azure-fundamentals/) |
| DP-900 Azure Data Fundamentals | [Microsoft Certified: Azure Data Fundamentals - Learn | Microsoft Docs](https://docs.microsoft.com/en-us/learn/certifications/azure-data-fundamentals/) |
| DP-203 Azure Data Engineer Associate | [Microsoft Certified: Azure Data Engineer Associate - Learn | Microsoft Docs](https://docs.microsoft.com/en-us/learn/certifications/azure-data-engineer/) |

In addition, Profisee recommends ongoing support from a Kubernetes Administrator for active project implementations.

## Database Maintenance

Profisee recommends regular database maintenance to ensure optimal system performance.

1. Depending on how often Matching and Survivorship, workflows, DQ rules and the like are processed, it is recommended to check the index fragmentation and rebuild during offline hours. Below is a script to check the index fragmentation on the DB. For best performance, it is recommended to keep the index fragmentation percent 30% or less.

```
SELECT
OBJECT_SCHEMA_NAME(ips.OBJECT_ID) 'Schema',
OBJECT_NAME(ips.OBJECT_ID) 'Table',
i.NAME,
ips.index_id,
index_type_desc,
avg_fragmentation_in_percent,
avg_page_space_used_in_percent,
page_count
FROM
sys.dm_db_index_physical_stats(DB_ID(), NULL, NULL, NULL, 'SAMPLED') ips
INNER JOIN
sys.indexes i
ON (ips.object_id = i.object_id)
AND
(
ips.index_id = i.index_id
)
ORDER BY
avg_fragmentation_in_percent DESC
```

2. It is recommended to set the history retention days to something that is reasonable. (e.g 60 days, 180 days, etc.) By default, the history logging level is set to 10 years. Clients can use the History Retention system setting to set the history retention period. Note that whenever clients set the history retention period, it will automatically start to run the cleanup script and delete all history entries that are older than x amount of days.
3. One other housekeeping best practice is to set the event logging retention period. Clients can find this in FastApp Studio by going to Settings -> System Settings -> Housekeeping. From there, clients can set the amount of days they wish to keep any event logs.
4. Lastly, if clients find that the logging.tSystemlog table is starting to fill up, there is a built in stored procedure in the SQL DB called logging.pPurgeLoggingMessages that will clean up the logging table with messages older than X amount of days.
5. For versions prior to 2022 R2, below is a script to check the amount of data across all entities in the Profisee DB. This can help identify large tables that potentially need to be cleaned up.

```
select schema_name(tab.schema_id) + '.' + tab.name as [table],
sum(part.rows) as [rows]
from sys.tables as tab
inner join sys.partitions as part
on tab.object_id = part.object_id
where part.index_id IN (1, 0) -- 0 - table without PK, 1 table with PK
group by schema_name(tab.schema_id) + '.' + tab.name
order by sum(part.rows) desc
```

6. Additional information on Database Indexing and Statistics maintenance automation: [Azure Automation: Automate Azure SQL Database indexes and statistics maintenance](https://www.sqlshack.com/automate-azure-sql-database-indexes-and-statistics-maintenance/) (sqlshack.com)
7. Additional PaaS deployment maintenance reference documentation: <https://support.profisee.com/wikis/profiseeplatform/maintenance_best_practices>

### See more

[Useful Commands for Cluster Management](https://support.profisee.com/wikis/profiseeplatform/Useful_Commands_for_Cluster_Management)