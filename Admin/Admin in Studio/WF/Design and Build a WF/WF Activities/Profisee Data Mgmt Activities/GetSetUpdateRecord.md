# GetSetUpdateRecord

The GetSetUpdateMember activity gets a member and sets the provided attribute values to a newly assigned value and updates it to the repository.

| | | |
| --- | --- | --- |
| **GetSetUpdateMember In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| MemberDataContext\* | [MemberDataContext](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type) | A **MemberDataContext**object containing information needed for the activity. |
| MemberValues | Dictionary<string, object> | A **Dictionary<String,Object>**object that a user can provide to set the Attribute(String) to a Value(Object). |
| AttributeNames | Collection<string> | A **Collection<String>** of all the Attribute Names; this is not a required argument. |
| **GetSetUpdateMember Out Arguments** | | |
| Result | [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type) | A **Member** object containing the updated values of each member attribute that was passed in utilizing the MemberValues. |
| Errors | Collection<Error> | A **Collection<Error>** that is returned if there are any abnormalities with the activity call. |

*\*Argument is required*

Note activities derived from CodeActivity<T> and NativeActivity<T> will always have a **Result** OutArgument<T> and zero or more other OutArguments. However, activities derived from CodeActivity and NativeActivity will not have a **Result** OutArgument<T>, but will have zero or more named OutArguments.

### Remarks

This activity gets the Attributes that exist within the Keys of the MemberValues and sets the Attributes to the passed in Value(s).

### See Also

- [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type)
- [Member Data Context](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type)