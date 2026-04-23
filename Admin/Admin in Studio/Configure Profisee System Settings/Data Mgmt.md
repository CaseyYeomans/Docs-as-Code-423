# Data Management

The table below displays the options and functions for Data Managementin System Settings.

| Option | Function |
| --- | --- |
| Background transaction monitor interval timer | The frequency, in minutes, of background master data transaction log inspections. The transaction monitor looks for changes that may have bypassed the platform API. |
| Batch size to send | The number of records sent at once to the server during publishing. A number between 2000 and 10000. |
| Data Quality Rule Processing Batch Size | The number of records evaluated and processed for rule assignments and violations. Recommended: 100000 to 200000. |
| Delete system-aware member | Delete system-aware member when the last system identifier has been deleted. There are two settings: - *False* - Off (Member is not deleted) - *True* - On (Member is deleted) |
| Entity members get max filter criteria count | The server limit for the maximum number of hierarchy members retrieved using "Edit Children," and the maximum number of members opened in a new tab when "Open this list in a new tab" is invoked from View Possible Matches. The maximum number for this value is determined by your system resources, but it is advisable to use the default setting. If no members are returned, use a lower setting. |
| History retention limit (days) | The number of days the system will retain logging. (Minimum 3 days) |
| Max response errors logged | The maximum amount of errors to be logged per request. If the value is set to -1, all errors will be logged. If the value is set to 0, no errors will be logged. If the value exceeds 0, the specified amount of errors will be logged per request. |
| Maximum Hierarchy Search Results | The maximum number of members returned when searching a hierarchy using a specified text pattern. The default value is 100. |
| Record Limit Warning Threshold | Percentage of record capacity used before a warning is triggered. |
| Sending sleep time | The length of time publishing waits before checking to see if there are additional records to send (in seconds). 5+ for low volume and 300+ for high volume are recommended settings. |
| Staging Parallelism | The number of concurrent threads (1-16) used on the application server to stream staged records to the database. This should not be set above the number of cores on the application or database server. |
| Writing error limit | The number of errors allowed before publishing stops. |