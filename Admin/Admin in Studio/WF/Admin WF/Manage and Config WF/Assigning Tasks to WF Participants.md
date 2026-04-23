# Assigning Tasks to Workflow Participants

Once a workflow has been registered and configured, the administrator can assign three types of activities to workflow participants:

- [Contribution Tasks](https://support.profisee.com/wikis/profiseeplatform/contribution_task)
- [Approval Tasks](https://support.profisee.com/wikis/profiseeplatform/approval_task)
- [Send Notification Tasks](http://support.profisee.com/wikis/profiseeplatform/send_notification)

When a task is assigned to a participant, they are notified to complete that task within a specified timeframe. Participants can be assigned as individual users, as part of a team, or as part of an assignment group.

To assign a task to workflow participants:

1. Open the [Workflow Configuration](https://support.profisee.com/wikis/profiseeplatform/configuring_workflows) window for a registered workflow.
2. Navigate to the **Details** tab.
3. Select the task you want to assign participants to.
4. Specify the Target Duration.
*The Target Duration is the amount of time allotted for this task to meet or exceed performance expectations. The task remains open until the Maximum Duration time is reached.*
5. Specify the Maximum Duration.
*The Maximum Duration is the maximum amount of time allotted for this task to complete. The task expires automatically if it does not complete in time.*
6. Select a value under the dropdown menu for Duration Scale.
*The Duration Scale defines the scale associated with the specified duration in seconds, minutes, hours, days, or weeks.*
7. Select a value under the dropdown menu for Notification Timing.
*The Notification Timing defines how quickly notifications are sent for this task once a specific task assignment is made.*
8. Select **User Assignment** and click the ellipsis icon to open the User Assignment window.
9. Select accounts from the Available Users field and use the Add arrow to move them into the Selected Users field.
10. Click **OK** to apply changes to User Assignment.
11. Click **Save** to apply changes to Task Assignment.

The User Assignment field displays the number of users assigned to that task. If a team has been added to the task assignment, the sum of the team is added to the user assignment field.

## Override Task Assignments by Assignment Group

Assignment Groups can be created to assign tasks to different users or teams than the default group if a member with a specific value is processed. A common use case for assignment groups is specifying geographic regions. If different users or teams need to manage data from different countries, you can create assignment groups to ensure members pertaining to those countries are assigned to their appropriate users or groups.

1. Open the User Assignment window for the task you want to configure.
2. Click the dropdown menu for Argument Value.
3. Select **<Create New>**.
4. Input a value in the Add New Value window.
5. Click **OK** to apply changes to the argument value.
6. Select accounts from the Available Users field and use the Add arrow to move them into the Selected Users field.
7. Click **OK** to apply changes to User Assignment.
8. Click **Save** to apply changes to Task Assignment.

Users in this assignment group will be assigned this task instead of the default group if a member contains the specified argument value.

Assignment groups can be further specified within Visual Studio. Composite assignment groups can be defined to receive tasks when a member contains one of several values. For example, an assignment group called "United Kingdom" could be created to receive a task when a member contains England, Wales, or Scotland for its Country value.

- If the same task is triggered in multiple assignment groups, a user who is listed in several of those groups will only receive one task.

- If a task is assigned to a team with no active accounts, the task falls back to assignees in the <default> group.

- If there is no default group or applicable assignment group to receive a task, the workflow is suspended and the task expires.

- You cannot assign an Entra/AD Group to a workflow, even if from a Team. Entra/AD Groups are filtered out because the user to which tasks should be assigned cannot be determined.