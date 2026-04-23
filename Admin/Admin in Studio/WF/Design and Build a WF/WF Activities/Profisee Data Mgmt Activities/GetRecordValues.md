# GetRecordValues

The GetRecordValues activity returns the values of the attributes from the declared Record.

| | | |
| --- | --- | --- |
| **GetRecordValues In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| AttributeNames\* | Collection<string> | A **Collection<string>** that represents an attribute of a Record. |
| Record\* | [Record](https://support.profisee.com/wikis/profiseeplatform/member_data_type) | A **Record** object. |
| **GetRecordValues Out Arguments** | | |
| RecordValues | Dictionary<string, object> | The **Dictionary<String,Object>** result of the operation. |

*\*Argument is required*

### Remarks

This activity logs any errors associated with the invalid input of the Attributes property.

### See Also

- [Get Record Value](https://support.profisee.com/wikis/profiseeplatform/get_member_value)
- [Record](https://support.profisee.com/wikis/profiseeplatform/member_data_type)