# CreateRecordBrowserContext

The CreateRecordBrowserContext activity creates a Record Browser Context that finds members using specified properties.

| | | |
| --- | --- | --- |
| **CreateRecordBrowserContext In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| PageNumber | int | The number of the page from which to retrieve the recorsd. This value defaults to 1. |
| PageSize | int | The amount of records to be retrieved. This value defaults to 50. |
| Filter | string | A **string** object representing an OData filter. For example [Color] ne 'Red' |
| OrderBy | string | A comma-separated list of attributes and directions to sort the returned records. Each attribute must be surrounded by brackets. For example, [MSRP] desc, [Color] asc |
| **CreateRecordBrowserContext****Out Arguments** | | |
| Result | RecordBrowserContext | The resulting **RecordBrowserContext** object to be used in another activity. |

*\*Argument is required*

Activities derived from CodeActivity<T> and NativeActivity<T> will always have a **Result** OutArgument<T> and zero or more other OutArguments. However, activities derived from CodeActivity and NativeActivity will not have a **Result** OutArgument<T>, but will have zero or more named OutArguments.

### Remarks

This activity creates a custom record browser context allowing the user to search for particular member(s) utilizing the provided properties.

**If you are experiencing performance issues:**
A RecordBrowserContext is often used to retrieve record data. By default, it will retrieve all attributes which exist in the entity for those retrieved records. It can be extremely beneficial to performance to change the defaults to limit the attributes retrieved. To accomplish this, create an **Assign** activity to set the Attributes property of the RecordBrowserContext to the limited attribute set. For example; setting the Attributes property to "[Code]" if you only need the codes to be returned, or "[Code],[Attribute1],[Attribute2]", etc.

###