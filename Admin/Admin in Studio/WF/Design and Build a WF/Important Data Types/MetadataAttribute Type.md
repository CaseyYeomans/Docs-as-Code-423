# MetadataAttribute Type

The **MetadataAttribute** type specifies all the column-level characteristics of an attribute as defined within an entity in the data model.

**Namespace:** Profisee.MasterDataMaestro.Services.DataContracts.MasterDataServices

### Properties

| | | | | |
| --- | --- | --- | --- | --- |
| | **Property Name** | | **Data Type** | **Description** |
| | | Id | Guid | A Globally-Unique Identifier (GUID) associated with this **MetadataAttribute** within the data model. *Inherited from Identifier* |
| | | InternalId | int | The Profisee instance-specific ID (surrogate key) for this **MetadataAttribute** in this platform instance. *Inherited from Identifier* |
| | | Name | string | The name given to this **MetadataAttribute** in the associated Entity. *Inherited from Identifier* |
| | | IsReferenceValid | bool | Indicates if the associated Id is valid. This is only used for metadata identifiers (e.g. [MaestroIdentifier](http://support.profisee.com/wikis/profiseeplatform/maestroidentifier_type)) and is not used for [MemberIdentifier](http://support.profisee.com/wikis/profiseeplatform/memberidentifier_type) instances. *Inherited from Identifier* |
| \* | | IsEmpty | bool | Indicates if this Identifier is semantically null (empty). *Inherited from Identifier* |
| | | AttributeType | [AttributeType](http://support.profisee.com/wikis/profiseeplatform/attribute_data_type) | Specifies the type of attribute associated with this **MetadataAttribute**. |
| | | AuditInfo | [AuditInfo](http://support.profisee.com/wikis/profiseeplatform/auditinfo_type) | Contains the audit details for this specific member. This includes the date and time as well as the users that created and last updated the member record. |
| | | Permission | [PermissionType](http://support.profisee.com/wikis/profiseeplatform/permissiontype_enumeration) | Specifies the permission that the current user has with respect to managing the value associated with this attribute. |
| | | DataType | [AttributeDataType](http://support.profisee.com/wikis/profiseeplatform/attributedatatype_enumeration) | Specifies the underlying data type when the **AttributeType** is set to **FreeForm**. |
| | | DataTypeInformation | int? | Specifies type-specific information for the attribute. If the **AttributeDataType** is **Text** or **Link**, then this field represents the maximum length of the associated text field. If the **AttributeDataType** is **Number**, then this field represents the decimal precision in the number of digits after the decimal point. |
| | | DisplayOrder | int | Specifies the default display order for attributes within the entity. |
| | | DisplayWidth | int | The width, in pixels, that should generally be used when presenting this attribute in a grid or on a form within FastApp Studio or Portal. |
| | | DomainEntityId | [Identifier](https://support.profisee.com/wikis/profiseeplatform/identifier_type) | If the AttributeType is Domain, then this indicates the entity to which the Domain-based Attribute (DBA) refers. |
| | | DomainEntityIsFlat | bool | **Obsolete** - Indicated that the entity contains an explicit hierarchy. **NOTE:** This field is a legacy artifact of Microsoft Master Data Services (MDS) support and is no longer used. |
| | | DomainEntityIsSystemAware | bool | Indicates that this attribute represents a System Aware Identity Management (SAIM) attribute which provides seamless association to record IDs in external systems. See also **ExternalSystemId**. |
| | | DomainEntityPermission | [PermissionType](https://support.profisee.com/wikis/profiseeplatform/permissiontype_enumeration) | Specifies the users access level on the entity associated with a Domain-based Attribute (DBA). |
| | | DoShowTime | bool | This setting applies when the **DataType** property is set to **DateTime**. It indicates if the time component of the **DateTime** is semantically relevant. |
| | | ExternalSystem | [MaestroIdentifier](http://support.profisee.com/wikis/profiseeplatform/maestroidentifier_type) | Identifies the external system to which this SAIM attribute is associated. See also **DomainEntityIsSystemAware**. |
| | | FullyQualifiedName | string | A string that represents the attribute name in combination with the entity name in dot notation. |
| | | HasDefault | bool | Indicates if the model indicates a default value should be used for this attribute. |
| \* | | IMetadataOjbect.Identifier | [Identifier](http://support.profisee.com/wikis/profiseeplatform/identifier_type) | Returns the **Identifier** associated with this **MetadataAttribute**. |
| | | InputMaskId | [Identifier](http://support.profisee.com/wikis/profiseeplatform/identifier_type) | **Obsolete** - Used to control input formatting in MDS. **NOTE:** This field is a legacy artifact of Microsoft Master Data Services (MDS) support and is no longer used. |
| | | IsAlwaysRequired | bool | |
| | | IsClearOnClone | bool | Indicates if this attribute should be automatically cleared (set to **null**) when its associated record is cloned in Studio or Desktop. |
| | | IsCode | bool | Indicates if this attribute is the **Code** attribute. |
| | | IsDate | bool | Indicates if this attribute is a date-only attribute. |
| | | IsDomain | bool | Indicates if this attribute is a DBA. |
| | | IsFile | bool | **Obsolete** - Indicates if this attribute is a File. **NOTE:** This field is a legacy artifact of Microsoft Master Data Services (MDS) support and is no longer used. |
| | | IsIndexed | bool | Indicates if there exists a database index on this attribute. By default, indexes exist on the **Code** attributes, all attributes where the **AttributeType** is Domain, and all attributes where **DomainEntityIsSystemAware** is true. Other user-defined attributes can be indexed as well. |
| | | IsMultiLevel | bool | Indicates whether this attribute exists on an entity that is not the main entity from which a [Member](http://support.profisee.com/wikis/profiseeplatform/member_data_type) object was read. See also [MultiLevelContext](http://support.profisee.com/wikis/profiseeplatform/multilevelcontext_type). |
| | | IsName | bool | Indicates whether this attribute is the **Name** attribute of the entity. |
| | | IsNumeric | bool | Indicates whether this attribute of **AttributeDataType.Number** |
| | | IsReadOnly | bool | Indicates whether this attribute is read-only from the perspective of the user the client is acting on behalf of. |
| | | IsRestricted | bool | Indicates whether this attribute is configured as **Restricted**. |
| | | IsString | bool | Indicates whether this attribute's underlying data type is **string**. |
| | | IsSystem | bool | Indicates whether this attribute is a system attribute. The **Code** and **Name** attributes are system attributes. All others are considered user-defined attributes. |
| | | IsUnique | bool | Indicates whether the values in this attribute must be unique within the associated entity. |
| | | LongDescription | string | Specifies a long description of this attribute for informational purposes. |
| | | MetadataObjectType | [MetadataObjectType](https://support.profisee.com/wikis/profiseeplatform/metadataobjecttype_enumeration) | An explicit indication that this artifact is a **MetadataAttribute (5)**. |
| | | ProfiseePermission | [SecurityPermissionType](http://support.profisee.com/wikis/profiseeplatform/securitypermissiontype_enumeration) | Specifies the permission the user on which the client is acting on behalf of has on the specific **MetadataAttribute**. |
| | | SortOrder | int | A 1-based index that indicates the current sort order of the results obtained on a read operation. |

\* *Getter only*

### Remarks

The **MetadataAttribute** type, when read from the server, includes both statically-defined properties of an attribute associated with an entity as well as dynamically-defined attributes that are a function of the current user attempting to work with the specified attribute. Broadly speaking, this type allows the client to understand the structure, data type, and security aspects of the attribute when metadata is obtained about an entity or when metadata is received as part of a data read operation on the server.

### See Also

- [Attribute Type](https://support.profisee.com/wikis/profiseeplatform/attribute_data_type)
- [AttributeType Enumeration](https://support.profisee.com/wikis/profiseeplatform/attributetype_enumeration)
- [AttributeDataType Enumeration](https://support.profisee.com/wikis/profiseeplatform/attributedatatype_enumeration)
- [AuditInfo Type](https://support.profisee.com/wikis/profiseeplatform/auditinfo_type)
- [Identifier Type](https://support.profisee.com/wikis/profiseeplatform/identifier_type)
- [MetadataObjectType Enumeration](http://support.profisee.com/wikis/profiseeplatform/metadataobjecttype_enumeration)
- [MaestroIdentifier Type](http://support.profisee.com/wikis/profiseeplatform/maestroidentifier_type)
- [SecurityPermissionType Enumeration](http://support.profisee.com/wikis/profiseeplatform/securitypermissiontype_enumeration)
- [PermissionType Enumeration](http://support.profisee.com/wikis/profiseeplatform/permissiontype_enumeration)