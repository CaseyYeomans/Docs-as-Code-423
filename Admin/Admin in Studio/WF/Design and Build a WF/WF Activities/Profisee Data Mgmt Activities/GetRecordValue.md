# GetRecordValue

The GetRecordValue activity returns the value of type <T> of the attribute from the declared Record.

| | | |
| --- | --- | --- |
| **GetRecordValue In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| Record\* | [Record](https://support.profisee.com/wikis/profiseeplatform/member_data_type) | A Record object. |
| Name\* | String | A **String** that represents an attribute of a Record. |
| **GetRecordValue Out Arguments** | | |
| Result | The data type of the attribute that is returned | The attribute value result of type **<T>.** |

*\*Argument is required*

Activities derived from CodeActivity<T> and NativeActivity<T> will always have a **Result** OutArgument<T> and zero or more other OutArguments. However, activities derived from CodeActivity and NativeActivity will not have a **Result** OutArgument<T>, but will have zero or more named OutArguments.

### Remarks

The returned value of type<T> is declared when the GetRecordValue activity is added to the Profisee workflow. The result returns null if the attribute specified in the Name property does not match any attributes of the Record.

### See Also

- [Record](https://support.profisee.com/wikis/profiseeplatform/member_data_type)