# SendNotification Activity

The SendNotification activity allows a workflow designer to send a notification to one or more users through Profisee's notification services. Users receive notifications in two ways:

- Via an email from the configured SMTP mail server
- Via notifications in the Portal, which can be viewed in full in the notifications page

| | | |
| --- | --- | --- |
| **SendNotification In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| Description | String | The text to include in the notification message to the recipients. |
| RecipientGroup | String | A text string that is used to parameterize the recipients to receive this notification. A recipient group can be used to alter the recipients based on data available to the workflow at runtime. The task management service. |
| NotificationType | String | Identifies the type of notification. This is an optional parameter and if not specified, the default value is set to "Notification". This allows the workflow to specify any string value you likes for the notification type. In addition, in digest emails, the notifications can be grouped by notification type. |
| OverrideRecipients | Collection<string> | A comma-separated list of user account names (e.g. "corporate\johnDoe" or "johnDoe@corporate.com") that should receive this notification. |
| AdditionalEmails | Collection<string> | Allows the activity to accept optional email lists. |

### Remarks

In order for SendNotification to send an email correctly, you must have an SMTP server address properly configured in FastApp studio. SendNotification behaves according to the task configuration in the workflow version configuration. Notifications can be [configured](https://support.profisee.com/wikis/profiseeplatform/configuring_send_notification_activities) to be sent immediately, in regular intervals, or never.

###