# Important Data Types for Workflow Developers

This topic briefly identifies common, important data types that developers working with workflows and the SDK will encounter.

### Properties

| | |
| --- | --- |
| **Data Type** | **Definition** |
| [Attribute Type](https://support.profisee.com/wikis/profiseeplatform/attribute_data_type) | Defines the structure and holds the value of a data attribute as it exists within the **Attributes** collection of a **Member** object. |
| [AttributeDataType Enumeration](https://support.profisee.com/wikis/profiseeplatform/attributedatatype_enumeration) | Defines the underlying logical data type of a **FreeForm** [MetadataAttribute](http://support.profisee.com/wikis/profiseeplatform/metadataattribute_type). |
| [AttributeType Enumeration](https://support.profisee.com/wikis/profiseeplatform/attributetype_enumeration) | Defines the major classification of data type of a [MetadataAttribute](http://support.profisee.com/wikis/profiseeplatform/metadataattribute_type) |
| [AttributeValueType Enumeration](https://support.profisee.com/wikis/profiseeplatform/attributevaluetype_enumeration) | Defines the underlying physical data type of a value [Attribute](http://support.profisee.com/wikis/profiseeplatform/attribute_data_type). |
| [AuditInfo Type](https://support.profisee.com/wikis/profiseeplatform/auditinfo_type) | Specifies the who created and last changed a member record or metadata artifact along with the time it was created and last changed. |
| [Identifier Type](https://support.profisee.com/wikis/profiseeplatform/identifier_type) | The base class of all identifier types within the platform. It provides the a name along with globally-unique as well as platform instance-specific IDs that uniquely identify the record within its respective repository. |
| [InvalidAttribute Type](https://support.profisee.com/wikis/profiseeplatform/invalidattribute_type) | A subclass of the value [Attribute](http://support.profisee.com/wikis/profiseeplatform/attribute_data_type) classification used to indicate if the associated value violated a constraint rule. |
| [MaestroIdentifier Type](https://support.profisee.com/wikis/profiseeplatform/maestroidentifier_type) | Provides underlying base data type used for identifying all Profisee-specific metadata and artifacts within a Profisee Platform instance. |
| [Member Type](https://support.profisee.com/wikis/profiseeplatform/member_data_type) | Defines the structure of a Member record when read from or written to the platform server. |
| [MemberDataContext Type](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type) | Specifies all of the information needed to read a member from the platform. It includes the [MemberIdentifier](http://support.profisee.com/wikis/profiseeplatform/memberidentifier_type) along with the entity ID in which the member resides. Represents the main input argument to a Workflow. |
| [MemberIdentifier Type](https://support.profisee.com/wikis/profiseeplatform/memberidentifier_type) | Specifies all of the identifying attributes of a member record including the **InternalId**, **Id**, **Name**, and **Code**. |
| [MetadataAttribute Type](https://support.profisee.com/wikis/profiseeplatform/metadataattribute_type) | Defines static and dynamic characteristics of an attribute as it exists within a given entity. |
| [ModelContextIdentifier Type](https://support.profisee.com/wikis/profiseeplatform/modelcontextidentifier_type) | A subclassification of Identifier that includes the model. |
| [MultiLevelContext Type](https://support.profisee.com/wikis/profiseeplatform/multilevelcontext_type) | Defines a relationship path to a specific [Attribute](http://support.profisee.com/wikis/profiseeplatform/attribute_data_type) that exists outside the entity from which a specific [Member](http://support.profisee.com/wikis/profiseeplatform/member_data_type) object was read. |
| [PermissionType Enumeration](https://support.profisee.com/wikis/profiseeplatform/permissiontype_enumeration) | The legacy MDS enumeration that identifies the permissions a specific user has on a given [MetadataAttribute](http://support.profisee.com/wikis/profiseeplatform/metadataattribute_type) in the system. |
| [SecurityPermission Enumeration](https://support.profisee.com/wikis/profiseeplatform/securitypermission_enumeration) | The legacy MDS enumeration that identifies the permissions a specific user has to on a given [Member](http://support.profisee.com/wikis/profiseeplatform/member_data_type) record in the system. |
| [SecurityPermissionType Enumeration](https://support.profisee.com/wikis/profiseeplatform/securitypermissiontype_enumeration) | The Profisee Platform-specific enumeration that identifies the permissions granted a user directly or indirectly through his or her Team or Active Directory group assignments. |
| [UpdateState Enumeration](https://support.profisee.com/wikis/profiseeplatform/updatestate_enumeration) | Specifies the action to be taken by the server when a specific data or metadata artifact is published to the server. |
| [ValidationStatus Enumeration](https://support.profisee.com/wikis/profiseeplatform/validationstatus_enumeration) | Indicates the data quality rule validation status of a member or attribute. |

###