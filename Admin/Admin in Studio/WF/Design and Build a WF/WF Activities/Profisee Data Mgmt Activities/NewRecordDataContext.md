# NewRecordDataContext

Given a member code, the NewMemberDataContext activity returns a new MemberDataContext object.

| | | |
| --- | --- | --- |
| **NewMemberDataContext****In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| Code | String | The member code string |

| | | |
| --- | --- | --- |
| **NewMemberDataContext Out Arguments** | | |
| MemberDataContext | MemberDataContext | The MemberDataContext object. |

### Remarks

The NewMemberDataContext activity accepts a member code string as an in argument. The NewMemberDataContext activity returns a new MemberDataContext object for the entity that can be used in the following workflow activity.

Note that the NewMemberDataContext and CreateMemberDataContext activities are identical, except that the NewMemberDataContext allows workflow administrators to dynamically set the entity after the workflow is registered in FastApp Studio in the workflow configuration, while the CreateMemberDataContext requires the entity name during workflow design/development time.

### See Also

[Create Member Data Context](https://support.profisee.com/wikis/profiseeplatform/create_member_data_context)