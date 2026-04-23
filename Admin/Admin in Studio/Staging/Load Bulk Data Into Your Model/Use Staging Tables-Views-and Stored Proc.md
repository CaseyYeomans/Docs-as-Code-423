# Use Staging Tables, Views, and Stored Procedures to Load Bulk Data

Batch integration administrators and authorized system processes such as ETL processes use the staging tables and related database artifacts to load data into your record data model. Refer to [Manage Staging Tables via FastApps Studio](https://support.profisee.com/wikis/profiseeplatform/manage_staging_tables_via_fastapps_studio) for details on creating a staging area for loading data.

Administrators create two types of staging tables to add, update, and delete data in your record data entities:

1. **Merge** creates and updates members in your entities.
2. **Delete** deletes members from your entities.

Follow this general process when staging data:

1. Start with an empty staging table. Load the staging table with the records that describe the changes that are to be made when those records are applied by the underlying entity tables.
2. Select from the staging view to ensure that there are no validation errors (e.g. where IsValid=0).
3. Invoke the staging table's associated stored procedure to apply the batch.

The user or credentials provided to run the stored procedure must either be a Profisee user with the **Batch Integration Administrator role** OR a non-Profisee user assigned the **stg\_exec database** or **dbo\*** role. If the staging table includes the option "enforce data quality constraint rules," you must use a Profisee user.

After invoking the stored procedure, a return code is displayed within SQL Server to indicate whether the batch was processed successfully or with errors. A return code of **0** indicates the batch was processed successfully, and a return code of **1** indicates the batch returned an error.

The staging tables content varies based on the Batch Type specified when configuring the staging tables in FastApps Studio. Refer to the following sections for how to perform each type of staging action:

- [Add and Update Data using a Merge Table](https://support.profisee.com/wikis/profiseeplatform/add_and_update_data_using_a_merge_table_8-0-1)
- [Delete Members using a Delete Table](https://support.profisee.com/wikis/profiseeplatform/delete_members_using_a_delete_table_8-0-1)

The staging tables can be populated using any technique in which rows can be inserted into a SQL table. This can include:

- Manual entry using SQL Server Management Studio (SSMS)
- Manually generated SQL scripts
- Programmatically using any programming or scripting language with a SQL Server-compatible database interface
- Using any variety of ETL tools such as SQL Server Integration Services (SSIS) or the like

Most customers adopt a formal and rigorously tested ETL process for large-scale, ongoing bulk loading in their production environments.

Note that you cannot run two staging jobs at the same time on the same entity.

### System Setting Notes

- The recommended maximum value for the **Batch size to send** system setting is 50,000.
- Audit, as well as any downstream processes such as business rules or eventing, are processed once the entire staging process is finished.
- The **Writing error limit** system setting defines how many errors can occur during bulk staging before processing ends. If the error limit is reached, all members remain within the staging table. Members that would not have been processed are removed from the staging table. If the error is related to a violation of a data quality constraint rule (and the **Enforce Data Quality Constraint Rules** option is selected), the codes of the members will be included in the event viewer detail.
- Calls to the API to load data via staging are multi-threaded. The **Staging Parallelism** system setting allows you to set the number of threads used to process staging. Do not set this limit above the number of threads your application server has available. Use caution when running multiple staging processes in parallel, as *each* process uses the number of threads specified by this setting.If you experience deadlocking during staging, this setting can be lowered to reduce the number of parallel database operations. Note that this will reduce performance. This setting can be increased to improve performance. Testing has shown that setting this above 4 has minimal improvements on performance as the database is limited in how many queries it can run in parallel against a given table.

## See Also

- [Staging Tables Overview](https://support.profisee.com/wikis/profiseeplatform/staging_tables_overview)