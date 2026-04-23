# SetRecordValue

The SetMemberValue activity sets a specified attribute of a Member.

| | | |
| --- | --- | --- |
| **SetMemberValue In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| Member\* | [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type) | A **Member** object containing information for the specified member with the attribute value that will change. |
| Name\* | String | A **String** that is the name of the Attribute of the Member. |
| Value\* | Object | An **Object** representing the value to set the value of the given attribute. |

*\*Argument is required*

### Remarks

This activity only sets the value of the attribute for the member and does not update the value in the repository. The UpdateMember task must be used to update a Member that has had a value set with SetMemberValue.

### See Also

- [UpdateMember](https://support.profisee.com/wikis/profiseeplatform/update_member)
- [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type)