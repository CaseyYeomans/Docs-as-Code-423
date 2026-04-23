# ApprovalTask Activity

The approval task prompts a workflow participant to approve or reject changes made to a piece of data by a contributor.

| | | |
| --- | --- | --- |
| **ApprovalTask In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| AssignmentGroup\* | string | A **String** value used to determine the collection of participants to which the task should be assigned. |
| OverrideAssignments\* | Collection<string> | A **Collection<String>** object used to assign users dynamically through the task properties. Teams cannot be assigned in this way. |
| RecordDataContext | RecordDataContext | A **RecordDataContext** object containing information needed for the task. |
| NotificationDescription | string | A **String** value used for the description column of the task in an email notification. |
| TaskDescription | string | A **String** value used for the description column of the task in a task list. |
| **ApprovalTask Out Arguments** | | |
| CompletedAssignments | Collection<WorkflowTaskAssignment> | A **Collection<WorkflowTaskAssignment>** object is returned to represent task assignments that participated in the task. |
| TaskStatus | TaskStatus | A **TaskStatus** object is returned with the value Canceled, Completed, Expired, Open, or Undefined. |
| TaskId | int | An **Integer** representing the ID of the current task. |
| Approved | bool | A **Boolean** value providing information on the approval of the Task; it is True if the task fulfilled the approval requirements, and False otherwise. |

*\*Argument is required*

### Remarks

The participant receives a form containing the necessary data to be approved once the prerequisite contribution has completed. Additionally, an approver can make changes to a piece of data they are assigned to approve.

To assign an approval task, you must add users to the list of assignees in the Workflow Configuration window within Profisee FastApps Studio.