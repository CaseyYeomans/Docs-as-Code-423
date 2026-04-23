# Staging Tables Overview

Staging is the process used to perform bulk loads of data to your master data model. Use staging to achieve the following goals:

- **Initial loading of your data model during the development of your master data management solution**. Early in development, it is common to load and re-load data as your model evolves during development. Staging is the fastest means of getting large amounts of data loaded into your model.
- **Ongoing batch integration with external systems**. Most analytical and operational master data management solutions have some form of ongoing batch integration, with data loaded in bulk on a periodic - typically daily - basis. The staging tables and related stored procedures provide the interface for ETL (Extract, Transform, and Load) processes to load data in bulk into your master data model.

## Staging Database Artifacts

A Staging Table is a place to load data changes at the database level before they are applied to your master data entities by the system. The system will ensure that data can be applied without error prior to processing and that an audit history is captured according to the Logging property of the entity.

Note that you cannot import artifacts from newer version of Profisee into older versions of Profisee.

**WARNING**: Never directly load or change data in the underlying data tables (i.e. tables in the data schema). Direct changes to the data schema are not supported.

[Staging Table](https://support.profisee.com/wikis/profiseeplatform/manage_staging_tables_via_fastapps_studio) administration facilitates management of staging tables and related artifacts used for bulk data loading. To manage staging tables, you must be granted the following roles and permissions:

- **Super Administrator** or **Batch Integration Administrator** through direct assignment.
- If you are granted only **Batch Integration Administration**, you must have **Administration** permission on an entity to manage its staging environment. This must be assigned through direct assignment.

Each staging table provides one of two possible data actions:

1. **Merge** creates and updates members in your entities.
2. **Delete** deletes members from your entities.

Each staging table is paired with a related set of database artifacts:

1. **View**: Use the view to verify whether a member of the table is going to be processed successfully before the batch is applied and locate any faulty data.
2. **Stored Procedure**: A staging stored procedure provides the logic that applies (loads) the data from the table into the underlying entity. You may execute the stored procedure directly to process the data when you want to orchestrate a complete loading process via SQL or ETL. The logic of the stored procedure varies by type of artifact (Merge or Delete).

The table below summarizes the combination of artifacts and artifact types and their respective purpose in the batch integration process:

| Artifact | Merge | Delete | |
| --- | --- | --- | --- |
| Table | Contains the records to be created or updated | Identifies the codes to be deleted | |
| View | Echoes the table content plus the forecasted validation status of create and update requests | Echoes the codes from the table plus the forecasted validation status of the delete requests | |
| Stored Procedure | Executes the merge batch as specified in the table | Executes the delete batch as specified in the table | |

All staging artifacts are stored in the **stg** schema in the database associated with the platform instance. The following figure illustrates the nine artifacts as they might appear for an entity called Customer for a batch integration administrator named John Smith. The names shown are examples only. You may define the names as desired; however, by best practice, the name chosen could reflect the target entity, action and purpose.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i6b65b5d43b676e65.png)

Each batch integration administrator can have his or her own staging artifacts that are separate from other administrators' artifacts. This minimizes the risks of administrators interfering with each other's efforts. Similarly, each source system process can have its own staging artifacts to avoid interference between those processes (e.g. stopping the load process for one source system does not prevent others from loading). You may choose to create tables for each source system under a designated system account, such that there is a clear audit trail of where the data came from.

## See Also

[Manage Staging Tables via FastApps Studio](https://support.profisee.com/wikis/profiseeplatform/manage_staging_tables_via_fastapps_studio)

[Use Staging Tables, Views, and Stored Procedures to Load Bulk Data](https://support.profisee.com/wikis/profiseeplatform/use_staging_tables_views_and_stored_procedures_to_load_bulk_data_8-0-1)

[Staging Batch Status Definitions](https://support.profisee.com/wikis/profiseeplatform/staging_batch_status_definitions)