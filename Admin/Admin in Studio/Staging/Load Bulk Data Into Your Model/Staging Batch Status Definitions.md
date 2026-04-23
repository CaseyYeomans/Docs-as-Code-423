# Staging Batch Status Definitions

The platform and various batch stored procedures track the status of staging batches before, during, and after the batches have been executed. The table below describes the various status values:

| Enumeration Value | Integer Value | Description |
| --- | --- | --- |
| Idle | 0 | The staging table has been created but has not been executed. |
| Started | 1 | A request to execute the batch has been received and pre-checks are in progress. |
| InvalidDataError | 2 | The batch stored procedure has determined that a data error has occurred and has stopped the batch execution. |
| Running | 3 | The batch has passed the pre-checks and the stored procedure is processing the batch. |
| Success | 4 | The batch has completed successfully. |
| Error | 5 | A SQL exception has occurred while processing the batch. If the batch was executed from FastApps Studio, or through an API call to the platform, the platform records the detail of the SQL exception to the Windows application event log. If the error occurs from a custom ETL process, the ETL process is responsible for recording the details of the SQL error for supportability purposes. The **Writing error limit**system setting defines how many errors can occur during bulk staging before processing ends. If the error limit is reached, all members remain within the staging table. Members that would not have been processed are removed from the staging table. If the error is related to a violation of a data quality constraint rule (and the **Enforce Data Quality Constraint Rules** option is selected), the codes of the members will be included in the event viewer detail. |
| ModelCheckoutError | 6 | The stored procedure has detected that the record data model is checked out for editing. This error occurs as a pre-check. Therefore, no attempt was made to process the data in the staging table. |
| PermissionError | 7 | The user does not have sufficient permissions, or is not recognized. |
| ErrorLimitExceeded | 8 | The maximum number of allowed errors has been exceeded. |