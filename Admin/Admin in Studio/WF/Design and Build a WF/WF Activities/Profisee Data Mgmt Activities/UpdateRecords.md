# UpdateRecords

The UpdateMembers updates a collection of records within the repository.

| | | |
| --- | --- | --- |
| **UpdateMembers In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| MemberDataContext\* | [MemberDataContext](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type) | A **MemberDataContext**object containing information needed for the activity. |
| Members\* | Collection<[Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type)> | The **Collection** of type **Member** containing the values to update. |
| **UpdateMembers Out Arguments** | | |
| Errors | Collection<Error> | A **Collection<Error>** object that returns empty if the operation was successful. |

*\*Argument is required*

Activities derived from CodeActivity<T> and NativeActivity<T> will always have a **Result** OutArgument<T> and zero or more other OutArguments. However, activities derived from CodeActivity and NativeActivity will not have a **Result** OutArgument<T>, but will have zero or more named OutArguments.

### Remarks

This task returns a collection of Error objects, indicating any failure that may have occurred during the update process. If the collection is empty, then the update was successful.

### See Also

- [UpdateRecord](https://support.profisee.com/wikis/profiseeplatform/update_member)
- [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type)
- [Member Data Context](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type)