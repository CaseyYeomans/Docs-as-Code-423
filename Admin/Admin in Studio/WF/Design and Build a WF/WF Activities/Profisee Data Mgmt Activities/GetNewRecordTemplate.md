# GetNewRecordTemplate

The GetNewMemberTemplate activity creates a MemberTemplate with a Name and Code in which a Member object is returned.

| | | |
| --- | --- | --- |
| **GetNewMemberTemplate In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| Name | String | A **String** value representing the Name of the Member. |
| Code | String | A **String** value representing the code of the Member. |
| **GetNewMemberTemplate Out Arguments** | | |
| Result | [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type) | A **Member** object that will be returned. |

*\*Argument is required*

Activities derived from CodeActivity<T> and NativeActivity<T> will always have a **Result** OutArgument<T> and zero or more other OutArguments. However, activities derived from CodeActivity and NativeActivity will not have a **Result** OutArgument<T>, but will have zero or more named OutArguments.

### Remarks

This activity creates a custom browse entity context allowing the user to search for particular member(s) utilizing the provided properties.

### See Also

- [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type)