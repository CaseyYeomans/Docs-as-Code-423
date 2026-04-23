# CopyRecordAttribute

The CopyRecordAttribute activity copies values between two attributes within a Record.

| | | |
| --- | --- | --- |
| **CopyRecordAttribute In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| FromAttributeName\* | String | A **String** value representing the attribute name that contains the value to be copied. |
| ToAttributeName\* | String | A **String** value representing the attribute name receiving the attribute value being copied. |
| Record | [Record](https://support.profisee.com/wikis/profiseeplatform/member_data_type) | A **Record** object containing information of the specified Record that will be added. |

*\*Argument is required*

### Remarks

The Record must not be null and must contain the attributes defined in the **FromAttributeName** and **ToAttributeName** properties.

### See Also

- [Record](https://support.profisee.com/wikis/profiseeplatform/member_data_type)