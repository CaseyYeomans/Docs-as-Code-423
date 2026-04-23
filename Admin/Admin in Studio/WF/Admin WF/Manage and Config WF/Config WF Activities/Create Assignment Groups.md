# Creating Assignment Groups

Every Task Activity configuration has a <default> Assignment Group that contains the list of users and teams that receive assignments when a task or notification is created. Additional Assignment Groups can be created to assign tasks to users or teams other than the <default> group based typically on values of the member or a related member being processed by an instance of a workflow. A common use case for assignment groups is varying the users and teams receiving assignments based on a specific geographic regions. For example, if different users or teams need to manage data from different countries, you can create assignment groups to ensure members pertaining to those countries are assigned to their appropriate users or groups.

1. Open the [Workflow Configuration](https://support.profisee.com/wikis/profiseeplatform/configuring_workflows) window for a registered workflow.
2. Navigate to the **Details** tab.
3. Select an activity that can be assigned to users or teams.
4. Select **User Assignment** from the Task Assignment field of the Workflow Configuration window**.**
5. Click the ellipsis icon to open the User Assignment window.
6. Click the dropdown menu for Argument Value.
7. Select **<Create New>**.
8. Input a value in the **Add New Value** window.
9. Click **OK** to apply changes to the argument value.
10. Select accounts from the Available Users field and use the Add arrow to move them into the Selected Users field.
11. Click **OK** to apply changes to User Assignment.
12. Click **Save** to apply changes to Task Assignment.

**NOTE**: The value specified in step 8 above is typically a **Code** value of a Domain-based Attribute (DBA) that is set on the member being processed. For example, it might be the Country Code of the country where a customer is headquartered allowing any changes for that customer to be directed to the account management team specified for that country. ***It is the responsibility of the workflow designer to specify the Assignment Group as an input argument to the [Contribution Task](https://support.profisee.com/wikis/profiseeplatform/configuring_contribution_and_approval_tasks), [Approval Task](https://support.profisee.com/wikis/profiseeplatform/configuring_contribution_and_approval_tasks), and [Send Notification](https://support.profisee.com/wikis/profiseeplatform/configuring_send_notification_activities)******activities****.*

Users in the specified assignment group will be assigned this task instead of the <default> group if the workflow processes a member containing the specified argument value. However, if the specified Assignment Group does not exist or has no members, the system will fall back to the <default> Assignment Group.

Assignment groups can be further specified within Visual Studio. Composite assignment groups can be defined to receive tasks when a member contains one of several values. For example, an assignment group called "United Kingdom" could be created to receive a task when a member contains England, Wales, or Scotland for its Country value.

- If the same task is triggered in multiple assignment groups, a user who is listed in several of those groups will only receive one task.

- If a task is assigned to a team with no active accounts, the task falls back to assignees in the <default> group.

- If there is no <default> group or applicable assignment group to receive a task, the workflow is suspended and the task expires.