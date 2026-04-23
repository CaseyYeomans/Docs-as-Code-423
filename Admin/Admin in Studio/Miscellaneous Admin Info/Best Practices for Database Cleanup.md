# Best Practices for Database Cleanup

Profisee recommends regular database maintenance to ensure optimal system performance.

- Depending on how often Matching and Survivorship, workflows, DQ rules etc. are processed, it is recommended to check the index fragmentation and rebuild during offline hours. Below is a script to check the index fragmentation on the DB. Keep in mind, for best performance, it is recommended to keep the index fragmentation percent around 30%.

```
SELECT OBJECT_NAME(Index_Info.OBJECT_ID) AS TableName
,Index_Info.name AS IndexName
,Index_Stat.index_type_desc AS IndexType
,Index_Stat.avg_fragmentation_in_percent IndexFragmPercent
FROM sys.dm_db_index_physical_stats(DB_ID(), NULL, NULL, NULL, NULL) Index_Stat
INNER JOIN sys.indexes Index_Info ON Index_Info.object_id = Index_Stat.object_id
AND Index_Info.index_id = Index_Stat.index_id
ORDER BY IndexFragmPercent DESC
```

- It is recommended to set the history retention days to something that is reasonable. (e.g 60 days, 180 days, etc.) by default, the history logging level is set to 3650 days. To manually set the history retention period, change the **History Retention Limit (Days)** setting in the Profisee System Settings. Whenever you set the history retention period, it will automatically start to run the cleanup script and delete all history entries that are older than x amount of days.
- You must also set the event logging retention period. You can find this in FastApp Studio by going to **Settings > System Settings > Housekeeping.** From there, you can set the amount of days you wish to keep any event/audit logs.
- If the logging.tSystemlog table is starting to fill up, there is a built-in stored procedure in the SQL DB called **logging.pPurgeLoggingMessages** that will clean up the logging table with messages older than *X* amount of days.