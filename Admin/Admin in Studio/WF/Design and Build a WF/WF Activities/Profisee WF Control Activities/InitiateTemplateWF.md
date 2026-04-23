# InitiateTemplateWorkflow

The InitiateTemplateWorkflow activity initiates a workflow without specifying a model and entity.

| | | |
| --- | --- | --- |
| **GetMember In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| MemberDataContext | MemberDataContext | A **MemberDataContext** object containing information needed for the task |
| **GetMember Out Arguments** | | |
| InitiatingUser | string | A **string** representing the Initiating User of the workflow. |

*\*Argument is required*

### Remarks

This activity does not create a MemberDataContext, which is necessary for many of the activities included in Profisee SDK Workflow Tools. This activity initiates a workflow without requiring a member code. You must create a new member data context to use other activities within the workflow.

###