# Configuring Contribution and Approval Tasks

Contribution and Approval tasks are sent to workflow participants via FastApps studio and prompt them to make changes to data or approve the changes made by other stewards.

To configure a contribution or approval task:

1. Open the [Workflow Configuration](https://support.profisee.com/wikis/profiseeplatform/configuring_workflows) window for a registered workflow.
2. Navigate to the **Details** tab.
3. Select the Contribution or Approval task you want to configure.

#### Activity Field

The activity field displays the version of Profisee FastApps Studio in which the workflow was created. If the workflow was imported from a different version than the version of Profisee you are running, the workflow process may encounter errors. If the Assembly Version is a higher version than the instance of Profisee you are running, it is recommended you upgrade the platform before continuing.

If desired, a user can add a description to the task that will be displayed to the workflow participants in their notifications.

#### Task Field

4. Select a previously configured [form](https://support.profisee.com/wikis/profiseeplatform/forms_overview).
*The information on this form will be displayed to the assigned users.*
5. Specify a priority level for the workflow.
*This value is user-defined and has no bearing on the operation of the workflow.*

#### Task Assignment Field

6. Specify the Approvals Required (Approval tasks only).
*The Approvals Required defines the minimum number of approvals required to complete and approve the task. This value must be greater than zero and less than or equal to the total number of assigned participants.*
7. Specify the Target Duration.
*The Target Duration is the amount of time allotted for this task to meet or exceed performance expectations. The task remains open until the Maximum Duration time is reached.*
8. Specify the Maximum Duration.
*The Maximum Duration is the maximum amount of time allotted for this task to complete. The task expires automatically if it does not complete in time.*
9. Select a value under the dropdown menu for Duration Scale.
*The Duration Scale defines the scale associated with the specified duration in seconds, minutes, hours, days, or weeks.*
10. Select a value under the dropdown menu for Notification Timing.
*The Notification Timing defines how quickly notifications are sent for this task once a specific task assignment is made.*

- *If set to **Immediate**, notifications are sent to participants when the task assignment is created.*
- *If set to **Never**, no notifications are sent to participants.*
- *If set to **Digest**, notifications are sent to participants at regular intervals. The length of this interval is controlled by the Notification Interval setting in System Settings. For more information, see [Configure Notifications](https://support.profisee.com/wikis/profiseeplatform/system_settings_notification).*

11. Select **User Assignment** and click the ellipsis icon to open the User Assignment window.

You can only assign tasks to individual accounts or teams. AD Groups cannot be used for workflow task assignments.

12. Select accounts from the Available Users field and use the Add arrow to move them into the Selected Users field.
13. Click **OK** to apply changes to User Assignment.
14. Click **Save** to apply changes to the activity.