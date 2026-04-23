# AttributeType Enumeration

The **AttributeType** enumeration identifies the major data type of its associated [MetadataAttribute](http://support.profisee.com/wikis/profiseeplatform/metadataattribute_type).

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts.MasterDataServices

### Properties

| | |
| --- | --- |
| **Enumeration Name** | **Description** |
| Not Specified=0 | The default value and should not be set for any defined **MetadataAttribute**. |
| FreeForm=1 | The associated attribute is a free-form attribute. A **FreeForm** attribute is one in which the, typically, users can enter free-form data that is only constrained by the underlying [AttributeDataType](http://support.profisee.com/wikis/profiseeplatform/attributedatatype_enumeration) and not by a constrained pick-list. |
| Domain=2 | The attribute value refers to another member record in the same or a different entity. A Domain-based Attribute (DBA) is effectively a foreign key to a different record. The entity to which the **Domain** attribute refers is defined by the **DomainEntityId** of the associated [MetadataAttribute](http://support.profisee.com/wikis/profiseeplatform/metadataattribute_type). The underlying value type associated with a Domain attribute is the [MemberIdentifier](http://support.profisee.com/wikis/profiseeplatform/memberidentifier_type) type. |
| System=3 | The attribute is a system-defined attribute. In the Profisee Platform, every entity in the data model has a **Name** and **Code** attribute. Both are considered **System** attributes. |
| File=4 | **Obsolete** - The associated attribute contains unstructured file data. **NOTE**: This value is a legacy value associated with Microsoft Master Data Services (MDS). File attributes have been replaced by **File Attachments** in the Profisee Platform. File Attachments do not use the **File** attribute. |

### Remarks

The **AttributeType** enumeration specifies the major data type classification for the attribute. This value helps clients determine the underlying [AttributeDataType](http://support.profisee.com/wikis/profiseeplatform/attributedatatype_enumeration) and, correspondingly, the underlying C# and SQL types associated with attribute.

### See Also

- [AttributeDataType Enumeration](https://support.profisee.com/wikis/profiseeplatform/attributedatatype_enumeration)
- [MemberIdentifier Type](https://support.profisee.com/wikis/profiseeplatform/memberidentifier_type)
- [MetadataAttribute Type](https://support.profisee.com/wikis/profiseeplatform/metadataattribute_type)