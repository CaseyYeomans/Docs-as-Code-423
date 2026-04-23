# Configure Event Housekeeping

The following settings in System Settings > Housekeeping control the Housekeeping process:

| Setting | Default value | Location | Description |
| --- | --- | --- | --- |
| **Maximum audit transactions per batch** | 50 | Profisee System Settings | The maximum number of rows that should be removed at a time by the audit housekeeping process. |
| Event message retention days | 45 (days) | Profisee System Settings | The **Event message retention days** setting controls the number of days an event message is stored after it is created. A message can be purged when the number of event retention days has passed, after midnight on the last day. After this date, the message is purged the next time housekeeping purges messages, regardless of message status. The valid range of values for this setting is 0 - 999. A value of 0 (zero) disables housekeeping and retention-based purges from the CLU. |
| Event message housekeeping processing interval | 600 (seconds) | Profisee System Settings | How frequently Profisee examines the housekeeping requests for housekeeping tasks to perform. |

Setting event message retention days to **0** disables event housekeeping. If a housekeeping request is issued through the CLU when the event message retention days is 0, the housekeeping request is ignored and no event data is purged.