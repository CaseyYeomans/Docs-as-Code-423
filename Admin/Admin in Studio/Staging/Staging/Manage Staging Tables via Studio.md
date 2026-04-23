# Manage Staging Tables via FastApps Studio

Manage your staging environment from FastApp Studio's **Administration** window. From the **Staging Tables** tab, you can perform the following activities:

- View the existing inventory of staging tables.
- Add a new staging table and its related artifacts.
- Edit an existing staging table.
- Delete existing staging tables.
- Process the records that have been staged into the staging table.

Staging Table administration in FastApp Studio does not provide access to load or view data in staging tables. Use common SQL tools such as SQL Server Management Studio to perform this task.

## View Staging Table Configurations

The **Staging Tables** tab in FastApp Studio lists all accessible staging tables. To see a staging table you must be:

- A **Super Administrator**

**--Or--**
- Assigned the **Batch Integration Administration** role, with **Administration** permission on the underlying entity

The list displays the staging tables you can access. The list contains the following columns:

| Column Name | Description |
| --- | --- |
| Table Name | The physical name of the table as defined within the stg schema of the Profisee database instance. |
| Entity | The name of the entity to which the staging table is associated. |
| Batch Type | Identifies if this table is used for Merg or Delete, when applied. |
| Status | Identifies the status of the batch. The following status values are possible: - Idle - Started - Invalid Data Error - Running - Success - Error - Model Checked Out For details definitions, refer to Staging Batch Status Definitions. |
| Row Count | Identifies the total number of records currently staged into the specific table. |
| Last Process Count | The number of records processed during the last successful processing of the batch. |
| Last Processed By | The domain user name that last requested execution of this batch. |
| Last Process Duration | The running time of the last batch execution in the format 'd h:m:s'. |
| Updated On | The last date and time that the definition of the staging table was altered. |
| Updated By | The domain user name of the last user to alter the staging table. |
| Created On | The date and time the staging table was created. |
| Created By | The domain user name of the user that created the staging table. |

By default, the list of staging tables is sorted by table name in ascending order. However, you can resort the table by clicking any header to alternate sorting in an ascending or descending order.

## Add a New Staging Table Configuration

Perform the following steps to add a new staging table configuration:

1. Click the **New**button. The staging table configuration panel opens.
2. Select the **Entity** to which you want to load data.

The list filters to the entities you can access for staging. Refer to [Staging Tables Overview](https://support.profisee.com/wikis/profiseeplatform/staging_tables_overview) for details.
3. Select the **Action** from the associated drop-down list.
4. Give the table a unique **Table name**.

FastApp Studio defaults the table name to {entity\_name}\_{action}. For example, if the entity name is Customer and the action is Merge, then the default table name is Customer\_Merge.

This may be confusing if multiple administrators work on the same entity. Add a third variable to better identify tables, such as Customer\_Merge\_{DomainName}.

5. Enter a **Description** (optional) to help other users understand the purpose of the table.
6. Set the **Process valid records when invalid records are present** option as desired. It is enabled by default.

When set, the batch process completes even if invalid records are encountered, disregarding those records.

If the option box is unchecked, the entire batch process will fail when an invalid record is found.

7. Set the **Clear contents after successful run** option as desired. It is enabled by default.

When set, the system truncates the staging table after the batch is successfully processed. This saves space and maintains the efficiency of the batch execution process.
8. Set the **Enforce data quality constraint rules** options as desired (if applicable). It is disabled by default.

When set, the system automatically applies data quality rules that are marked as constraints when the staging table is processed. Any members which violate constraint rules are skipped, all other members (including those in the batch) are processed successfully, and the members who violated those constraint rules are left behind, even when the **Clear contents** option is applied.

9. Navigate to the **Attributes** tab.
10. Select which attributes to include in the staging table from the attributes list. If all are desired, click **Select All**. To deselect all attributes, click **Clear All**.

If new attributes should be included in the staging table after they are added, select **Include in staging table** under **Default Behavior for New Attributes**.

11. Set null handling preferences. Refer to [Null Handling and Auto Add DBAs in Staging Table Configurations](https://support.profisee.com/wikis/profiseeplatform/null_handling_and_auto_add_dbas_in_staging_table_definitions) for more information concerning settings.
12. Click **Save**or **Save and close** to store the staging table configuration and to create its related artifacts in the database.

Note that two staging tables cannot create members in the same entity at the same time when both entities have the **Create code values automatically** setting enabled.

## Add a New Bulk Staging Table Configuration

Perform the following steps to add a new bulk staging table configuration:

1. Click the **New (Bulk)**button. The New Staging Tables (Bulk) configuration panel opens.
2. Double click all entities to which you want to load data. Alternatively, select all desired entities and click the right-facing arrow button.
3. Click **Next.**
4. Select the **Action** from the associated drop-down list.
5. Enter a prefix or suffix in the Staging Table Name field to give the table a unique name. The default convention for the table name is [Blank Prefix][Entity Name][\_Action].
6. Enter a **Description** (optional) to help other users understand the purpose of the table.
7. Navigate to the Process Options field and select any of the following options.

- **Process valid records when invalid records are present**: Invalid records are not processed when the table is processed.
- **Clear contents after successful run**: Clears all contents after the staging table is processed successfully.
- **Enforce data quality constraint rules**: Automatically applies data quality rules that are marked as constraints when the staging table is processed.

8. Navigate to the Existing Attribute options field and select preferences for [null handling and domain values](https://support.profisee.com/wikis/profiseeplatform/null_handling_and_auto_add_dbas_in_staging_table_definitions) for attributes that already exist within the entity.
9. Navigate to the New Attribute Options field and select preferences for [null handling and domain values](https://support.profisee.com/wikis/profiseeplatform/null_handling_and_auto_add_dbas_in_staging_table_definitions) for new attributes that are added to the entity.
10. Click **Create**.

## Edit a Staging Table Configuration

Perform the following steps to change a staging table configuration:

1. Select an existing staging table configuration in the grid and click the **Edit**button.

The staging table configuration panel opens to display current configuration. The **Entity** and **Action** fields are disabled. These cannot be changed once the staging table configuration has been created.
2. Change the Table name if desired.

The table name must be unique within the system. **A table name may be in use by an entity you cannot access**, which will not display with tables listed in the staging table configurations grid. It's rare, but possible.
3. Enter a **Description** (optional) to help other users understand the purpose of the table.
4. Set the **Process valid records when invalid records are present** option as desired. It is enabled by default.

When set, the batch process completes even if invalid records are encountered, disregarding those records. If the option box is unchecked, the entire batch process will fail when an invalid record is found.

5. Set the **Clear contents after successful run option** as desired. It is enabled by default.

When set, the system truncates the staging table after the batch is successfully processed. This saves space and maintains the efficiency of the batch execution process. You may also clear the data clear the table as a step in your SQL or ETL process (e.g. using a TRUNCATE TABLE or DELETE FROM in SQL).
6. Set the **Enforce data quality constraint rules** options as desired (if applicable). It is disabled by default.

When set, the system automatically applies data quality rules that are marked as constraints when the staging table is processed.

7. Click **Save**or **Save and close** to store the staging table configuration and to create its related artifacts in the database.

## Delete Staging Table Configurations

You can delete any staging table configuration you can access. Deleting the staging table configuration deletes the following information:

- All loaded data
- All artifacts related to the staging table configuration, including table, view, and stored procedure

Perform the following steps to delete a staging table configuration :

1. Select one or more rows in the staging table configurations grid.
2. Click **Delete**. A confirmation dialog opens, warning that deleting a staging table removes all of the content in that table.
3. Click **Yes** to confirm. Click **No** to cancel the delete operation.

Once you have confirmed that it is okay to delete the table(s), a processing indicator appears while the delete operation is processed. Once the delete is complete, the rows are removed from the staging table configurations grid.

## Manually Process and Clear a Staging Table

Batch Integration Administrators can request processing of the data batch in any staging table they can access.

Perform the following steps to process a staging batch:

1. Click the Process drop-down menu button on the Staging Tables toolbar.

The two options are **Process**, which starts the batch; and **Clear**, which truncates all of the records currently in the associated staging table.
2. Click **Process**. A confirmation dialog window opens.
3. Click **Yes** to confirm launching of the batch process execution. Click **No** to cancel the launch of the batch process.

The server processes the batch asynchronously in the background. Click **Refresh**in the main toolbar to see the status of the batch.

Perform the following steps to clear the content from an existing table:

1. Click the Process drop-down menu button on the Staging Tables toolbar.
2. Click **Clear**. A confirmation dialog window opens.
3. Click **Yes** to confirm. Click **No** to cancel the clear request.

The server processes the clear operation asynchronously in the background.

## See Also

[Use Staging Tables, Views, and Stored Procedures to Load Bulk Data](https://support.profisee.com/wikis/profiseeplatform/use_staging_tables_views_and_stored_procedures_to_load_bulk_data_8-0-1)