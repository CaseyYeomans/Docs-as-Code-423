# SetRecordValues

The SetMemberValues activity sets a specified attributes of a Member.

| | | |
| --- | --- | --- |
| **SetMemberValues In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| DisplayName\* | String | The name of the current instance of this activity. This appears in the title of the activity on the workflow design surface. |
| Member\* | [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type)\* | A **Member** object containing information for the specified member with the attribute value that will change. |
| MemberValues\* | Dictionary<string, object> | A **Dictionary<string,object>** type representing the <attributeName,value> to set the values of the given attributes. |

*\*Argument is required*

### Remarks

This activity only sets the value of the attribute for the member and does not update the value in the repository. The UpdateMember task must be used to update a Member that has had a value set with SetMemberValue.

### See Also

- [UpdateMember](https://support.profisee.com/wikis/profiseeplatform/update_member)
- [SetMemberValue](https://support.profisee.com/wikis/profiseeplatform/set_member_value)
- [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type)