# UserTask

The **User** task creates a task and its related assignments and is implemented in both the processes of [Contribution](https://support.profisee.com/wikis/profiseeplatform/contribution_task_activity) and [Approval](https://support.profisee.com/wikis/profiseeplatform/approval_task_activity) tasks.

| | | |
| --- | --- | --- |
| **UserTask In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| AssignmentGroup\* | string | A **String** value used to determine the collection of participants to which the task should be assigned. |
| OverrideAssignments\* | Collection<string> | A **Collection<String>** object used to assign Participants dynamically through the task properties. |
| MemberDataContext | MemberDataContext | A **MemberDataContext** object containing information needed for the task. |
| NotificationDescription | string | A **String** value used for the description column of the task in an email notification. |
| TaskDescription | string | A **String** value used for the description column of the task in a task list. |
| **UserTask Out Arguments** | | |
| CompletedAssignments | Collection<WorkflowTaskAssignment> | A **Collection<WorkflowTaskAssignment>** object is returned to represent task assignments that participated in the task. |
| TaskStatus | TaskStatus | A **TaskStatus** object is returned with the value Canceled, Completed, Expired, Open, or Undefined. |
| TaskId | int | An **Integer** representing the ID of the current task. |

*\*Argument is required*

### Remarks

Note that this is simply the implementation logic of the main functions of both Approval and Contribution tasks which creates a task and its related assignments and is not an activity that you can use in the workflow.

### See Also

- [G](https://support.profisee.com/wikis/profiseeplatform/new_member_data_context_activity)[et Members](https://support.profisee.com/wikis/profiseeplatform/get_members)
- [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type)
- [Member Data Context](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type)