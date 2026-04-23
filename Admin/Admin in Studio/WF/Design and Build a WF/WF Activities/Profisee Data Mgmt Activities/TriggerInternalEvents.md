# TriggerInternalEvents

The TriggerInternalEvents activity allows workflow developers to trigger real-time event processing from within a workflow activity.

| | | |
| --- | --- | --- |
| **TriggerInternalEvents In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| RecordDataContext\* | [RecordDataContext](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type) | A RecordDataContext object containing information needed for the task. |
| EventNames\* | Collection<string> | A **Collection<string>** representing the names of the events to be triggered. |
| RecordCodes | Collection<string> | A **Collection<string>** representing the codes of the records for the events to be triggered for. |
| **TriggerInternalEvents Out Arguments** | | |
| Errors | Collection<Error> | A **Collection<Error>** object that returns empty if the operation was successful. |

*\*Argument is required*

### Remarks

If the MemberCodes collection is empty, the member code value will default to the code supplied by the MemberDataContext argument. If the UserName argument is empty, then the user name value will default to the initiating user.

###