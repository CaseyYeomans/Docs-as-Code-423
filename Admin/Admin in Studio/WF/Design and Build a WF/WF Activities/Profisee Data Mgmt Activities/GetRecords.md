# GetRecords

The GetRecords activity gets a set of records from the repository and returns them in the form of a Collection<Record> object.

| | | |
| --- | --- | --- |
| **GetRecords In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| RecordDataContext\* | RecordDataContext | A **RecordDataContext** object containing information needed for the activity. |
| RecordBrowserContext | RecordBrowserContext | A **RecordBrowserContext** object that specifies search, filter, and ordering characteristics of the desired result set. |
| **GetRecords Out Arguments** | | |
| Records | Collection<Record> | A collection of type **Record.** |

*\*Argument is required*

Activities derived from CodeActivity<T> and NativeActivity<T> will always have a **Result** OutArgument<T> and zero or more other OutArguments. However, activities derived from CodeActivity and NativeActivity will not have a **Result** OutArgument<T>, but will have zero or more named OutArguments.

### Remarks

The **GetRecords** activity reads a Collection of type record from the Profisee server and returns the collection in the form of a **Collection<****Record>** object. If the user sets GetValidationIssues to true, then a dictionary of dictionaries will be returned with the operation result representing a set of validation issues for the collection of records. The RecordDataContext for this activity does not need a Record Code to retrieve a Collection of Records. The returned collection is empty if there are no records in the entity or no records matching the filter criteria specified in the BrowseEntityContext property.

### See Also

- [G](https://support.profisee.com/wikis/profiseeplatform/new_member_data_context_activity)[et Record](https://support.profisee.com/wikis/profiseeplatform/get_member)
- [Record](https://support.profisee.com/wikis/profiseeplatform/member_data_type)
- [Record Data Context](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type)