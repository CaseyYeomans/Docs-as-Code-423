# InitiateWorkflow

The InitiateWorkflow activity initiates a workflow without specifying a model and entity.

| | | |
| --- | --- | --- |
| **GetMember In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| Entity\* | String | A **String** representing the Entity of the MemberDataContext. |
| RecordDataContext | MemberDataContext | A **RecordDataContext** object containing information needed for the task |
| **GetMember Out Arguments** | | |
| InitiatingUser | string | A **string** representing the Initiating User of the workflow. |

*\*Argument is required*

### Remarks

This activity does not create a MemberDataContext, which is necessary for many of the activities included in Profisee SDK Workflow Tools. This activity initiates a workflow without requiring a member code. You must create a new member data context to use other activities within the workflow. As of version 2021.R2, this activity can support multiple configurations.

###