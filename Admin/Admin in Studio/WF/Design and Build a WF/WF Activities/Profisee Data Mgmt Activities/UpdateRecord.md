# UpdateRecord

The UpdateRecord activity updates an existing record in the repository.

| | | |
| --- | --- | --- |
| **UpdateRecord In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| RecordDataContext\* | [RecordDataContext](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type) | A **RecordDataContext**object containing information needed for the activity. |
| Record | [Record](https://support.profisee.com/wikis/profiseeplatform/member_data_type) | A **Record** object containing the attribute values for the record. |
| **UpdateRecord Out Arguments** | | |
| Errors | Dictionary<string,List<string>> | A **Collection<Error>** object that returns empty if the operation was successful. |

*\*Argument is required*

Activities derived from CodeActivity<T> and NativeActivity<T> will always have a **Result** OutArgument<T> and zero or more other OutArguments. However, activities derived from CodeActivity and NativeActivity will not have a **Result** OutArgument<T>, but will have zero or more named OutArguments.

### Remarks

This task updates a record with new values specified in the record Attributes property. The task returns an error in the Collection<Error> collection if the Code property of the record RecordIdentifier property doesn't exist within the version specified within the RecordDataContext.

### See Also

- [Update Records](https://support.profisee.com/wikis/profiseeplatform/update_records)
- [Record](https://support.profisee.com/wikis/profiseeplatform/member_data_type)
- [Record Data Context](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type)