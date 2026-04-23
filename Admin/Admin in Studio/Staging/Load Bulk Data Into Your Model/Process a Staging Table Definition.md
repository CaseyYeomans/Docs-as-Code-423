# Process a Staging Table Definition

To process a staging table definition:

1. Navigate to **Administration | Staging Tables**.
2. Select a staging table definition in the list.
3. Click **Process** to open the Process menu on the staging tables toolbar.
4. Click **Process** on the menu.

The action in the staging table definition is executed using the configured staging table and target entity.

## Data Quality Rules Run Automatically on Staged Members

When a staging table is processed, any data quality rules that apply to entities in the table run automatically when the transaction is executed. The [background transaction monitor interval timer](https://support.profisee.com/wikis/profiseeplatform/data_management) and [housekeeping processing interval](https://support.profisee.com/wikis/profiseeplatform/housekeeping) settings determine how often staging transactions are checked.

## Rules Run Automatically On Newly Created Staged Members

Staged transactions run automatically on newly created members. Staging transactions are checked based on the background transaction monitor interval timer settings. Like interactive member updates, the rules process ignores assignment rules where Auto Update is turned off.

Logging should be set to capture enough information to inform administrators when assignment rules are not configured properly. The Event log displays a write event for each transaction and each batch.

## Eventing Triggers Automatically on Assignment Rule Changes

Eventing processes transactions created when assignment rules affect the entity.

## Processing Considerations

- If the error returned is a sql error (e.g. processing a delete staging table) with members in use OR processing a merge staging table that violates a unique constraint (option configured in modeling), the entire transaction will be rolled back so both valid and invalid members included in the transaction are unchanged. The individual member codes are not included in the event viewer detail, but detail about the problem is included.
- Insertion of staging records and processing of staging batches requires direct connection and access to the underlying Profisee database. This access should be provided with the minimum possible permissions to avoid inadvertent tampering with internal tables or possible security breaches. SQL Administrators can grant minimal permissions to a specific table, view and procedure or grant broad access to the stg schema. For example, create a role with Select, Insert, Delete, Execute to the stg schema and grant this role to the developer and background processing accounts.
- When attempting to process a large staging batch that affects matching or survivorship, you must pause continuous matching (if enabled) until the batch finishes processing. Once finished, it is recommended to run an incremental matching strategy on the staging batch before re-enabling continuous matching.

## See Also

[Staging Tables Overview](https://support.profisee.com/wikis/profiseeplatform/staging_tables_overview)

[Manage Staging Tables via FastApps Studio](https://support.profisee.com/wikis/profiseeplatform/manage_staging_tables_via_fastapps_studio)