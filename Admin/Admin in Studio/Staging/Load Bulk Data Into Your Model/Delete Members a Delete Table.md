# Delete Members Using a Delete Table

A **Delete** table allows you to delete members identified by the **Code** value supplied for each record in the batch. The following subsections describe the database artifacts associated with a **Delete** staging table configuration.

## The Delete Table

Delete tables are located in the **Tables** folder when looking at the configured Profisee database using SQL Server Management Studio (SSMS). Every delete table has the following naming convention:

stg.t{staging\_table\_configuration\_name}

Every delete table contains the following standard columns:

| Column | Description | Data Type |
| --- | --- | --- |
| ID | An identity column assigned by SQL server that uniquely identifies that row in the batch. | int, not null |
| Code | The primary business key associated with the member. The Code column contains a unique index and therefore, a specific code value can exist only once per batch. The code of an existing member must be supplied. | nvarchar(250), not null |

## The Delete View

A **delete view** is created when a Batch Integration Administrator creates a delete staging table configuration. The delete view has the following naming convention and appears in the **Views** folder of the configured Profisee database in SSMS:

stg.v{staging\_table\_configuration\_name}

The delete view echoes the information in the associated delete table and allows you to assess whether there are any issues **before** the batch is applied. The delete stored procedure uses the delete view to validate the batch before it is applied (see The Delete Stored Procedure).

The table below details the standard columns that appear in the delete view:

| Column | Description | Data Type |
| --- | --- | --- |
| ID | The internal ID of the existing member in the entity or NULL if the specified Code value cannot be found in the associated entity table. This is considered a data error and will cause the batch to fail to run. | int |
| \_#IsValid#\_ | Identifies if the record is valid and if the delete will succeed when applied. A value of 1 indicates the record is valid. A value of 0 indicates that the record is invalid and will not process correctly. | int |
| Code | Contains the Code value specified in the delete table for the member to which the delete record applies. This is a mandatory field and must be unique within the batch. | nvarchar(250) |

The \_#**IsValid#\_** column is set to 0 (false) when the **Code** value cannot be found in the associated entity data table.If any records in the batch are not valid and the **Ignore Invalid Records** staging table option is not selected, the batch fails to run and the **Status** value is set to **2 [InvalidDataError]**.

## The Delete Stored Procedure

The **delete stored procedure** is used by your ETL process as well as by the platform server itself to execute the current delete batch and to perform the actual deleting of data in the associated entity based on the content of the delete table.

The delete stored procedure has the following naming convention and appears in the **Stored Procedures** folder of the configured Profisee database in SSMS:

stg.p{staging\_table\_configuration\_name}

The delete stored procedure takes **no parameters** and returns the value of 0 when processing of the batch is successful or a value of 1 if the stored procedure fails for any reason.

The delete stored procedure performs the following pre-checks before attempting to process the data in the delete table:

- The batch is examined to see if any of the records in the associated delete view have the**\_#IsValid#\_** column set to 0 (false). If any records are invalid and the **Ignore Invalid Records** staging table option is not selected, the batch will not run and status of the batch is set to **2 [InvalidDataError]** (see also [Staging Batch Status Definitions](https://support.profisee.com/wikis/profiseeplatform/staging_batch_status_definitions)).
- The model is examined to see if it is checked out by a user through **Advanced Modeling** (see also [Releasing a checkout](https://support.profisee.com/wikis/profiseeplatform/release_a_checkout) ). If the model is checked out, the batch fails to run and the status is set to **6 [ModelCheckOutError]**.
- The batch is examined to see if it is already running. If two or more users try to run the same batch at the same time, only the first request is honored. Any subsequent requests are ignored and the stored procedure returns 0 (success).

Once the pre-checks are complete, the delete stored procedure performs processes the in the associated delete table. The application of the batch results in the following:

- Members in the associated entity table are deleted.
- History records are created according to the logging configuration specified for the associated entity (see Logging options in the [Creating entities](https://support.profisee.com/wikis/profiseeplatform/create_entities) section of Advanced Modeling for details).
- Updates the **Status, Last Processed Count, Last Processed On, Last Processed By**, and **Last Process Duration** audit properties once complete.

If a SQL exception occurs during batch processing, the batch's status is set to **5 [Error]**. Any exception information is logged to the Windows event log when the batch execution is requested through FastApps Studio or through the server API using the SDK.

When your custom ETL process requests batch execution, any SQL exception returned to the ETL process is the responsibility of that ETL process to capture and log for supportability purposes.

## See Also

- [Manage Staging Tables via FastApps Studio](https://support.profisee.com/wikis/profiseeplatform/manage_staging_tables_via_fastapps_studio)
- [Stage Batch Status Definitions](https://support.profisee.com/wikis/profiseeplatform/staging_batch_status_definitions)
- [Add and Update Data using a Merge Table](https://support.profisee.com/wikis/profiseeplatform/add_and_update_data_using_a_merge_table)