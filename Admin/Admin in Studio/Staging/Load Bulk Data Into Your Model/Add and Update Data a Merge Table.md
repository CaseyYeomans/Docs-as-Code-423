# Add and Update Data Using a Merge Table

Add new members to an entity if the specified member Code does not exist, and update members with existing Codes using a **Merge** batch. The structure of a merge batch table is identical to it associated entity table, from a column name perspective.

## The Merge Table

Merge tables are located in the **Tables** folder when looking at the configured Profisee database using SQL Server Management Studio (SSMS). Every merge table has the following naming convention:

stg.t{staging\_table\_configuration\_name}

The merge table contains the following standard columns:

| Column | Description | Data Type |
| --- | --- | --- |
| ID | An identity column assigned by SQL server that uniquely identifies that row in the batch. | int, not null |
| Code | The primary business key associated with the member. The Code column contains a unique index and therefore, a specific code value can exist only once per batch. See note below for further details. | nvarchar(250), not null -or- nvarchar(250), null |
| Name | The optional user-friendly name associated with the member. | nvarchar(250), null |
| NewCode | A column that can be used to update an existing record (per the **Code** column) to have an updated Code value. | nvarchar(250), not null -or- nvarchar(250), null |

The **Code** column of a merge batch table varies depending on whether the associated entity is configured with the **Create Code values automatically setting enabled**. If the entity is configured for code generation, the Code column of the staging batch is nullable. Otherwise, the Code column is not nullable. Refer to [Edit Entities](https://support.profisee.com/wikis/profiseeplatform/edit_entities) for details.

In addition to the standard columns above, a merge batch table contains a nullable column matching the name and data type of each user-defined attribute that exists in the associated entity table.

When applied, each record in a merge batch causes the creation or update of a member in the associated entity table. If the **Code** value is specified in the batch table, and that value already exists in the associated entity, the row results in an update operation. If the **Code** value does not exist, the row results in a create operation. This is sometimes referred to as an "upsert" operation.

It is important to note these rules when staging data for the following data types:

- Domain-based Attributes (DBA): When staging in a new or updated DBA attribute, you must specify the **Code** value that relates to the member in the associated domain entity table.
- DateTime: When staging in a DateTime attribute, the value of should be specified in UTC format. The batch process **does not** handle conversion of a DateTime attribute from local to UTC time.

The table below defines the expected result for create and update operations when the column value is null and non-null.

| Member | Column Content | |
| --- | --- | --- |
| Operation | **Non-NULL** | **NULL** |
| Create | defines attribute's original value | attribute's original value is NULL |
| Update | replaces attributes current value | leaves attributes current value unaltered, unless the **Apply Nulls** option is checked for this attribute in which case it is cleared. |

You can delete an attribute value using a merge batch by selecting the "Apply Nulls" option for the attribute in the staging table on the **Attributes** tab.

## The Merge View

A **merge view** is created when a Batch Integration Administrator creates a merge staging table configuration. The merge view has the following naming convention and appears in the **Views** folder of the configured Profisee database in SSMS:

stg.v{staging\_table\_configuration\_name}

Using merge view, you can:

1. Assess potential issues **before** the batch is applied. The **merge stored procedure** uses the merge view to validate the batch before it is applied.
2. If there are issues, identify which records and which domain-based attributes have reference errors.
3. See which records result in an insert or update.
4. See effective changes before the batch is applied.

The table below details the standard columns that appear in the merge view:

| Column | Description | Data Type |
| --- | --- | --- |
| ID | The internal ID of the existing member in the entity or NULL if this merge record results in creating a new member. | int |
| \_#IsValid#\_ | Identifies if the record is valid and if the merge will succeed when applied. A value of 1 indicates the merge record is valid. A value of 0 indicates that the record is invalid and will not merge correctly. | int |
| IsNew | Identifies if the merge record is going to result in a new member or an update to an existing member. A value of 1 indicates the record is new. A value of 0 indicates the record exists and the merge results in an update. | int |
| Code | Contains the Code value specified in the merge table. | nvarchar(250) |
| NewCode | Can be used to update an existing record (per the **Code** column) to have an updated Code value. | nvarchar(250) |
| Name | Shows what the Name value will be after processing. It contains either (a) the Name value as specified in the associated merge table or (b) the Name value from the associated entity data table if the Name value for the record in the merge table is NULL. | nvarchar(250) |
| **\_#IsNewCodeValid#\_** | Shows the validity of a new code value. If the new member is valid, the code displays a 1. If the new member is not valid, it displays a 0 and will not merge correctly. | |
| \_#IsNetChange#\_ | Shows whether or not the member has changed. If the member has changed, it displays a 1. If it has not changed, it displays a 0 and will not process. | |
| \_#IsDBAValid#\_ | identifies if DBA record values included in the staging table are valid. A value of 1 indicates the value is valid and the merge should result in an update. A value of 0 indicates the value is invalid and will not merge correctly. (e.g. if the domain value does not exist and the option to 'Add Domain Values' does not exist on the merge staging table.) | |

The merge view contains columns for each user-defined attribute in the entity. The name of the column matches the name of the user-defined attribute. The following rules define content of the user-defined columns:

- **Free-form attributes** (e.g. Text, Date, DateTime, Link, or Number) - the merge view column shows what the final value will be after processing. It contains either (a) the value specified in the merge table for that attribute if non-NULL, or (b) the value from the entity data table.
- **Domain-based attribute (DBA)** - the following additional rules apply:
- If a non-NULL value is specified for the attribute in the merge table **and** the value specified exists in the associated domain entity, then the value that appears in the view is the code value in the domain entity.
- If a non-NULL value is specified for the attribute in the merge table **and** the value specified **does not exist** in the associated domain entity, then the value that appears in the view is blank. If the option to **Add Domain Values** is specified, this may be valid.
- If a NULL value is specified for the attribute in the merge table, then the merge view contains NULL (with the option on the attribute to apply nulls) OR the value in the data table is NULL.

The following validation is performed by the merge view and will cause the **IsValid** column to be set to 0 (false):

- Any non-NULL DBA attributes specified in the merge table cannot be found in the associated domain entity if the **Add Domain Values** option is not specified.

## The Merge Stored Procedure

The **merge stored procedures** is used by your ETL process to execute the current merge batch and perform the actual data load from the merge table to the target entity.

The merge stored procedure has the following naming convention and appears in the **Stored Procedures** folder of the configured Profisee database in SSMS:

*stg.p{staging\_table\_configuration\_name}*

The merge stored procedure takes **no parameters** and returns the value of 0 when processing of the batch is successful or a value of 1 if the stored procedure fails for any reason.

The merge stored procedure performs the following pre-checks before attempting to load the data in the merge table:

- The batch is examined to see if any of the records in the associated merge view have the **IsValid** column set to 0 (false). If any records are invalid and the **Process Valid Records** option is not checked, the batch will not run and status of the batch is set to **2 [InvalidDataError]** (see also [Staging Batch Status Definitions](https://support.profisee.com/wikis/profiseeplatform/staging_batch_status_definitions)).
- The model is examined to see if it is checked out by a user through Advanced Modeling (see also [Release a checkout](https://support.profisee.com/wikis/profiseeplatform/release_a_checkout)). If the model is checked out, the batch fails to run and the status is set to 6 [ModelCheckOutError].
- The batch is examined to see if it is already running. If two or more users try to run the same batch at the same time, only the first request is honored. Any subsequent requests are ignored and the stored procedure returns 0 (success).

Once the pre-checks are complete, the merge stored procedure performs the data load to the associated entity data table. The application of the batch results in the following:

- Members are created and updated according to the content specified in the merge table.
- History records are created according to the logging configuration specified for the associated entity (see Logging options in the [Create entities](https://support.profisee.com/wikis/profiseeplatform/create_entities) section of Advanced Modeling for details).
- Updates the batch's **Status, Last Processed Count, Last Processed On, Last Processed By**, and **Last Process Duration** values once complete.

If a SQL exception occurs during batch processing, the batch's status is set to **5 [Error]**. Any exception information is logged to the Windows event log when the batch execution is requested through FastApps Studio.

When your custom ETL process requests batch execution, any SQL exception returned to the ETL process is the responsibility of that ETL process to capture and log for supportability purposes.

## See Also

- [Manage Staging Tables via FastApps Studio](https://support.profisee.com/wikis/profiseeplatform/manage_staging_tables_via_fastapps_studio)
- [Stage Batch Status Definitions](https://support.profisee.com/wikis/profiseeplatform/staging_batch_status_definitions)