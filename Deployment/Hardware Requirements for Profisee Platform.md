# Hardware Requirements for Profisee Platform

### Hardware Sizing Guide

| | | | | | | | | | | |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | **APP** | | | **SQL\*** | | | **Matching** | | | **Bulk Scoring** |
| **Records (M)** | **vCores** | **RAM (GB)** | **Storage (GB)** | **vCores** | **RAM (GB)** | **Storage (GB)** | **Worker Count** | **Cluster Records Batch Limit** | **Bulk Scoring Batch Limit** | **Default Partition Count** |
| 1 | 4 | 16 | 128 | 4 | 16 | 200 | 10 | 2 | 2 | 1 |
| 5 | 8 | 32 | 128 | 8 | 32 | 400 | 10 | 3 | 3 | 2 |
| 10 | 8 | 96 | 256 | 12 | 64 | 600 | 0 | 4 | 3 | 2 |
| 20 | 16 | 192 | 256 | 16 | 128 | 800 | 0 | 5 | 4 | 3 |
| 30 | 16 | 256 | 256 | 20 | 128 | 1000 | 0 | 6 | 4 | 3 |
| 40 | 32 | 384 | 256 | 24 | 256 | 1200 | 0 | 7 | 6 | 4 |
| 50 | 32 | 512 | 256 | 24 | 256 | 1400 | 0 | 8 | 6 | 4 |

Increasing the App Settings on the Matching and Matching.BulkScoring services will use more processor cores and memory and should only be used if processing initial matching or larger datasets. For most incremental workloads, the minimum/default settings should be sufficient. The default settings will use the minimum amount of cores and memory required to run matching, and will be the most cost-efficient. The recommendations are based on Profisee internal testing and can be adjusted over time.

*\*The recommendations assume that the SQL Server will be dedicated to hosting only the Profisee DB, and not other databases. It is not recommended the SQL Server be shared with other databases. If the SQL Server is shared, the recommended sizing should be provisioned per database.*

To adjust the settings you will have to modify the appsettings.json file for the Matching and Matching.BulkScoring services. After the values are adjusted you can recycle the Profisee-Matching and Profisee-BulkScoring App pools in IIS.

### OnPrem/IaaS

When deploying Profisee Platform on a Windows VM the files and settings can be found here:

Path to file: "C:\Program Files\Profisee\Master Data Maestro Server\25.2.0\Services\Matching\appsettings.json"

Setting:

"WorkerCount": 10
"ClusterRecordsBatchLimit": 2
"BulkScoringBatchLimit": 2

Path to file: "C:\Program Files\Profisee\Master Data Maestro Server\25.2.0\Services\Matching.BulkScoring\appsettings.json"
Setting:

"DefaultPartitionCount": 1

### PaaS

Customers using Kubernetes to deploy Profisee Platform must apply the settings in a Post Init script so they are not overwritten by the default app settings on each pod restart.

Example Post Init entry:

```
# Update Matching service settings
$pathToJson = "C:\profisee\services\matching\appsettings.json"
$a = Get-Content $pathToJson | ConvertFrom-Json
$a.ProfiseeAppSettings.WorkerCount = 10
$a.ProfiseeAppSettings.ClusterRecordsBatchLimit = 2
$a.ProfiseeAppSettings.BulkScoringBatchLimit = 2
$a | ConvertTo-Json -Depth 3 | Set-Content $pathToJson
# Recycle Matching service App Pool
c:\windows\system32\inetsrv\appcmd recycle apppool Profisee-Matching

# Update Matching.BulkScoring service settings
$pathToJson = "C:\profisee\services\Matching.BulkScoring\appsettings.json"
$a = Get-Content $pathToJson | ConvertFrom-Json
$a.ProfiseeAppSettings.DefaultPartitionCount = 1
$a | ConvertTo-Json -Depth 3 | Set-Content $pathToJson
# Recycle Matching.BulkScoring App Pool
c:\windows\system32\inetsrv\appcmd recycle apppool Profisee-BulkScoring
```