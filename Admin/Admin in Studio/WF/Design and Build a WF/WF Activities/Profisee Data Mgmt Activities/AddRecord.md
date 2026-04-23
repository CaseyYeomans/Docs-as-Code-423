# AddRecord

The AddRecord activity adds a new record to the Model and Entity specified in the RecordDataContext and provides its record Identifier as the result.

| | | |
| --- | --- | --- |
| **Addrecord In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| RecordDataContext\* | RecordDataContext | A **RecordDataContex**t object containing information needed for the task. |
| Record\* | Record | A **R****ecord** object containing information of the specified record that will be added. |
| **AddRecord Out Arguments** | | |
| Errors | Collection<Error> | A **Collection<Error>** object that returns empty if the operation was successful. |
| RecordIdentifier | RecordIdentifier | A **RecordIdentifier** object identifying the ID, Code, Name, and other key fields of a record. |

*\*Argument is required*

Activities derived from CodeActivity<T> and NativeActivity<T> will always have a **Result** OutArgument<T> and zero or more other OutArguments. However, activities derived from CodeActivity and NativeActivity will not have a **Result** OutArgument<T>, but will have zero or more named OutArguments.

### Remarks

If a variable is defined for the Errors property and the AddRecord activity is successful, the collection is empty. If there were application-level errors during the activity, then the Error collection contains one or more Error objects describing the error that occurred.

The AddRecord activity requires a [RecordDataContext](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type) with a valid Entity. The record to be added must not share a code that already exists within the database. It is not possible to add a record with a duplicate code.

### See Also

- [Record Identifier](https://support.profisee.com/wikis/profiseeplatform/memberidentifier_type)
- [Record](https://support.profisee.com/wikis/profiseeplatform/member_data_type)
- [Record Data Context](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type)