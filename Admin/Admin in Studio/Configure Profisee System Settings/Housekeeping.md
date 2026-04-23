# Housekeeping

The table below displays options and functions for Housekeeping in System Settings.

| Option | Function |
| --- | --- |
| Event message housekeeping process interval. | How frequently Profisee examines the housekeeping requests for tasks to perform (in seconds). |
| Event message retention days | The age, in days, after which an event is deleted from an internal or external event queue. The age of an event is calculated by looking at the creation date and time of the event, and subtracting this from the next midnight after the purge request creation date and time. If that age in days is greater than the configured retention date, the event is deleted. |
| Maximum audit transactions per batch | The maximum number of rows that should be removed at a time by the audit housekeeping process. |