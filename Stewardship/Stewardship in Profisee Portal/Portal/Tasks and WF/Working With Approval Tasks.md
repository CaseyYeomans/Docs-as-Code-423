# Working With Approval Tasks

The Approval Task gives an assignee the ability to approve or reject data changes made by other users or processes. An approver can change values in the Approval Task Form to which they are granted update rights. There are four options available to an approver once the Approval Task is visible:

- **Approve**: Advises the workflow to approve the changes made to the specified record and allow the workflow to continue processing.
- **Reject**: Advises the workflow to reject the changes made to the specified record and allow the workflow to continue processing.
- **Cancel**: Close the Form and return to the Task List.

Approving and rejecting changes from the Task List does not directly roll back any of the proposed changes. This responsibility lies with the associated workflow and how it is designed to react to approvals and rejections. The approvals and rejections from the users merely act as "advice" to the workflow. What the workflow does with that advice is at the sole discretion of the workflow designer.

Approval Tasks can be configured to require multiple approvals. In such cases, approving a change may not immediately complete the task if the task is waiting on multiple approvers. However, rejecting a change completes the task for all assignees and the workflow continues immediately.

To open a task in your task list within FastApp Portal, click on the task to open the associated Form.

### See More

- [**Configuring Workflows**](https://support.profisee.com/wikis/profiseeplatform/configuring_workflows)
- [**Configuring and Assigning Workflow Activities**](https://support.profisee.com/wikis/profiseeplatform/configuring_and_assigning_workflow_activities)