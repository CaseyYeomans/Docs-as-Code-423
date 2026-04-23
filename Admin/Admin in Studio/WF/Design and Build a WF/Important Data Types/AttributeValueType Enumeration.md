# AttributeValueType Enumeration

The **AttributeValueType** enumeration identifies the underlying data type associated with a value [Attribute](http://support.profisee.com/wikis/profiseeplatform/attribute_data_type).

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts.MasterDataServices

### Properties

| | |
| --- | --- |
| **Enumeration Name** | **Description** |
| Not Specified=0 | The default value and should not be set for any defined [MetadataAttribute](http://support.profisee.com/wikis/profiseeplatform/metadataattribute_type). |
| String=1 | The underlying type in the Value property of the **Attribute** is a string. |
| Number=2 | The underlying type in the Value property of the **Attribute** is a double. |
| DateTime=3 | The underlying type in the Value property of the **Attribute** is a DateTime. |
| Domain=4 | The underlying type in the Value property of the **Attribute** is a [MemberIdentifier](http://support.profisee.com/wikis/profiseeplatform/memberidentifier_type). |
| File=5 | **Obsolete** - The associated Value property of the **Attribute** contains unstructured file data. **NOTE**: This value is a legacy value associated with Microsoft Master Data Services (MDS). File attributes have been replaced by **File Attachments** in the Profisee Platform. File Attachments do not use the **File** attribute. |

### Remarks

When data is received from or sent to the server, a [Member](http://support.profisee.com/wikis/profiseeplatform/member_data_type) object carries the record information in its Attributes collection. Each Attribute in the collection has a value. The underlying type of that value is specified using the **AttributeValueType** enumeration. This enumeration is similar, but not identical, to the [AttributeDataType](http://support.profisee.com/wikis/profiseeplatform/attributedatatype_enumeration) enumeration that is associated with the [MetadataAttribute](http://support.profisee.com/wikis/profiseeplatform/metadataattribute_type) class.

### See Also

- [AttributeDataType Enumeration](https://support.profisee.com/wikis/profiseeplatform/attributedatatype_enumeration)
- [AttributeType Enumeration](http://support.profisee.com/wikis/profiseeplatform/attributetype_enumeration)
- [Attribute Type](http://support.profisee.com/wikis/profiseeplatform/attribute_data_type)
- [Member Type](http://support.profisee.com/wikis/profiseeplatform/member_data_type)
- [MemberIdentifier Type](https://support.profisee.com/wikis/profiseeplatform/memberidentifier_type)
- [MetadataAttribute Type](https://support.profisee.com/wikis/profiseeplatform/metadataattribute_type)