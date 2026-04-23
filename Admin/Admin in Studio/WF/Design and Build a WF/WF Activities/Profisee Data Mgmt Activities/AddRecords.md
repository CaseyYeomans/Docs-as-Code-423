# AddRecords

The AddRecords activity adds new Records to the entity specified in the RecordDataContext and returns a Collection of Errors if the operation was not successful.

| | | |
| --- | --- | --- |
| **AddRecords In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| RecordDataContext\* | RecordDataContext | A **RecordDataContext** object containing information needed for the task. |
| Records\* | Colleciton<Record> | A **Collection<Record>** that holds the new Records that will be added to the RecordDataContext. |
| **AddRecords Out Arguments** | | |
| Errors | Collection<Error> | A **Collection<Error>** object that returns empty if the operation was successful. |
| RecordIdentifiers | Collection<RecordIdentifier> | A **Collection<RecordIdentifier>** object identifying the ID, Code, Name, and other key fields of the Records selected. |

*\*Argument is required*

### Remarks

If a variable is defined for the Errors property and the AddRecords activity is successful, the collection is empty. If there were application-level errors during the activity, then the Error collection contains one or more Error objects describing the error that occurred.

The AddRecords activity requires a RecordDataContext with a valid Model, Entity, and Version. The Records to be added must not share codes that already exist within the database. It is not possible to add a Record with a duplicate code.

### See Also

- [Record Identifier](https://support.profisee.com/wikis/profiseeplatform/memberidentifier_type)
- [AddRecord](https://support.profisee.com/wikis/profiseeplatform/add_member)
- [Record Data Context](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type)