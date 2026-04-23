# ContributionTask Activity

The contribution task prompts a workflow participant to make changes to a piece of data within Profisee FastApps Portal.

| | | |
| --- | --- | --- |
| **ContributionTask In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| AssignmentGroup\* | string | A **String** value used to determine the collection of participants to which the task should be assigned. |
| OverrideAssignments\* | Collection<string> | A **Collection<String>** object used to assign users dynamically through the task properties. Teams cannot be assigned in this way. |
| RecordDataContext | RecordDataContext | A **RecordDataContext** object containing information needed for the task. |
| NotificationDescription | string | A **String** value used for the description column of the task in an email notification. |
| TaskDescription | string | A **String** value used for the description column of the task in a task list. |
| **ContributionTask Out Arguments** | | |
| CompletedAssignments | Collection<WorkflowTaskAssignment> | A **Collection<WorkflowTaskAssignment>** object is returned to represent task assignments that participated in the task. |
| TaskStatus | TaskStatus | A **TaskStatus** object is returned with the value Canceled, Completed, Expired, Open, or Undefined. |
| TaskId | int | An **Integer** representing the ID of the current task. |

*\*Argument is required*

### Remarks

The participant receives a form containing the necessary data to be altered once the task is assigned to them. After the contribution has been made, the workflow progresses to the next step.

To assign a contribution task, you must add users to the list of assignees in the [Workflow Configuration](https://support.profisee.com/wikis/profiseeplatform/configuring_workflows) window within Profisee FastApps Studio.