# AttributeDataType Enumeration

The **AttributeDataType** enumeration identifies the underlying data type for **Free Form** attributes.

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts.MasterDataServices

### Properties

| | |
| --- | --- |
| **Enumeration Name** | **Description** |
| Not Specified=0 | The default value and should not be set for any defined **MetadataAttribute**. |
| Text=1 | The associated attribute is of type text which translates to the **string** data type in C# and a **nvarchar** in SQL. |
| Number=2 | The associated attribute is a numeric data type which translates to a **double** in C# and a **decimal(x,y)** in SQL where y is the number of decimal points requested when configuring the attribute and x = 38 -y. Refer to the **DataTypeInformation** property of the [MetadataAttribute](http://support.profisee.com/wikis/profiseeplatform/metadataattribute_type) for more details. |
| DateTime=3 | The associated attribute includes both date and time elements. This translates to the C# **DateTime** type and the SQL **datetime(2,3)** type. |
| Date=4 | The associated attribute is a date-only attribute. This translates to the C# **DateTime** and SQL **date** data types. |
| Link=5 | The associated attribute is a hyperlink attribute. This translates do the C# **string** data type and the SQL **nvarchar** data type. |

### Remarks

The **AttributeDataType** enumeration specifies subtype of the attribute when the [AttributeType](http://support.profisee.com/wikis/profiseeplatform/attributetype_enumeration) of the [MetadataAttribute](http://support.profisee.com/wikis/profiseeplatform/metadataattribute_type) is set to **FreeForm**. Free form attributes are those attributes that users and provide in a free form manner, meaning they are not specified from a domain pick list. There are 5 types of free form attributes:

- Text
- Number
- DateTime
- Date
- Link

When a free form attribute type is created in modeling, the administrator must choose the underlying **AttributeDataType** for that free form attribute.

### See Also

- [AttributeType Enumeration](https://support.profisee.com/wikis/profiseeplatform/attributetype_enumeration)
- [MetadataAttribute Type](https://support.profisee.com/wikis/profiseeplatform/metadataattribute_type)