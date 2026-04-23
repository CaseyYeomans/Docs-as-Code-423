# ReverseRecordTransaction

The ReverseRecordTransaction activity allows workflow designers to (typically) reverse the transaction that is undergoing processing and review by a workflow. This allows the workflow to react to a rejection related to an ApprovalTask and undo the changes that triggered the workflow.

| | | |
| --- | --- | --- |
| **ReverseRecordTransaction In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| RecordDataContext\* | RecordDataContext | The RecordDataContext includes the EntityId, RecordID, and TransactionID for the activity. This property is derived from the [InitiateWorkflow](https://support.profisee.com/wikis/profiseeplatform/initiate_workflow) activity. A new RecordDataContext can be created using the [CreateRecordDataContext activity](https://support.profisee.com/wikis/profiseeplatform/create_member_data_context). |

| | | |
| --- | --- | --- |
| **ReverseRecordTransaction Out Arguments** | | |
| Result | MaestroOperationResult | Identifies the success or failure of the operation along with any errors that may have occurred on failure. |

*\*Argument is required*

### Remarks

When a workflow is initiated via Real-time Event Processing, one of the arguments passed to the workflow is the RecordDataContext that triggered the event. If that event was triggered due to a data change, the RecordDataContext argument's TransactionId property is set to the data transaction that triggered the event. Therefore, a workflow has, at its disposal, the EntityId, RecordId, and TransactionId that identify the changes to reverse.

Because the event will be generated after ReverseRecordTransaction completed due to nature of Real-time Event Processing, it is recommended to have a attribute rule that only allow ReverseRecordTransaction if certain attribute value fulfilled. For example, setting up "shouldReverseRecord" attribute and set the attribute rule to 'true' will prevent this activity from having infinite loop.

###