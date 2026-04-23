# Monitor Event Housekeeping Requests

Use SQL Server Management Studio (SSMS) to query the system for event housekeeping request status.

Execute the following query to view status information:

meta.vSYSTEM\_HOUSEKEEPING\_EVENT\_PURGE\_REQUEST

The query returns the following information:

| Column | Description |
| --- | --- |
| **ID** | Identifies an individual housekeeping service activity. All purge requests that are processed by the same housekeeping activity have the same ID. |
| **UID** | Unique identifier for individual housekeeping activities. |
| **EventPurgeRequestID** | Identifies an individual event purge request. A single housekeeping activity can process multiple event purge requests. |
| **EventPurgeRequestUID** | Unique identifier for individual purge requests. |
| **Request Type** | The type of purge request. Possible request types include: 1: EventPurgeAllByRetentionDays Event messages will be purged based on the Event message retention days setting. 2: EventPurgeSubscriberConfiguration Event messages will be purged for a subscriber configuration. 4: EventPurgeScenario Event messages will be purged for a scenario. 8: EventPurgeSubscription Event messages will be purged for a subscription. |
| **Status** | Possible request statuses include: 1: ReadyToProcess The purge request has been submitted and is waiting for the housekeeping service to run. 2: Processing The housekeeping service is currently processing the purge request. 8: Success The purge request competed successfully. 4: Error The purge request did not complete successfully. |
| **EventSourceType** | Identifies whether the event messages are Profisee events or an external events. 0: Profisee 1: Other |
| **EventScenarioID** | The identifier for the scenario associated with a purge request. |
| **EventScenarioUID** | The unique identifier assigned to an event scenario associated with a purge request. |
| **EventScenarioName** | The name of an event scenario associated with a purge request. |
| **SubscriberConfigurationID** | The identifier for the subscriber configuration associated with a purge request. |
| **SubscriberConfigurationUID** | The unique identifier of the subscriber configuration associated with a purge request. |
| **SubscriberConfigurationName** | The name of the subscriber configuration associated with a purge request. |
| **MinMessageSubscriberID** | The message with the lowest number in the range of event messages that will be purged. |
| **MaxMessageSubscriberID** | The message with the highest number in the range of event messages that will be purged. |
| **DeleteAfterPurge** | Indicates whether the associated event processing component will be deleted after the messages are purged. For example, when DeleteAfterPurge=True and the RequestType is EventPurgeScenario, then the scenario will be deleted after the associated event messages are purged. 1: True 0: False |
| **PurgeRequestRecordCount** | Estimated number of records that will be purged by the request. |
| **PurgedRecordCount** | Total number of messages purged so far (while the Status is Processing) or the total number processed by the request (when the Status is Success). |
| **RestartedCount** | Number of times that processing on a request was restarted due to server or service interruptions. If the service is interrupted while a request is processing, any event message with a status of Error or Processing is reset to a status of ReadyToProcess when the service starts again. |
| **ProcessStartDTM** | Starting date and time that the housekeeping request runs. This parameter is blank until the process runs. |
| **ProcessEndDTM** | Ending date and time that the housekeeping request completes. |
| **ErrorMessage** | Indicates any failure condition that occurred during processing of the housekeeping request. |
| **EnterDTM** | Date and time that the request was created. |
| **EnterUserID** | User ID of the user creating the request. |
| **EnterUserDisplayName** | Display name of the user creating the request. |
| **LastChgDTM** | Date and time of the last update to the housekeeping request. |
| **LastChgUserID** | User ID associated with the date and time the last change occurred. |
| **LastChgUserDisplayName** | Display name associated with the date and time the last change occurred. |

When housekeeping processes a purge request that deletes a scenario or subscriber configuration, the values will appear NULL for EventScenarioID and EventScenarioName, or for SubscriberConfigurationUID and SubscriberConfigurationName after the request finishes processing.

To monitor progress during a purge, check the PurgedRecordCount value to see how many messages have been processed so far.