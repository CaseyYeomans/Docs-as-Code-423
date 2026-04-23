# Attribute Type

The **Attribute** class represents the value of an attribute within a given [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type) record.

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts.MasterDataServices

### Properties

| | | | |
| --- | --- | --- | --- |
| | **Property Name** | **Data Type** | **Description** |
| | Id | Guid | A Globally-Unique Identifier (GUID) associated with this member in the Entity. *Inherited from Identifier* |
| | InternalId | int | The Profisee instance-specific ID (surrogate key) for this Entity member in this platform instance. *Inherited from Identifier* |
| | Name | string | The name given to this member in the associated Entity. *Inherited from Identifier* |
| | IsReferenceValid | bool | Indicates if the associated Id is valid. This is only used for metadata identifiers (e.g. MaestroIdentifier) and is not used for [MemberIdentifier](http://support.profisee.com/wikis/profiseeplatform/memberidentifier_type) instances. *Inherited from Identifier* |
| \* | IsEmpty | bool | Indicates if this Identifier is semantically null (empty). *Inherited from Identifier* |
| | Value | object | The object that represents the value of this Attribute. The type of object associated with the Attribute depends on its **Type** property. |
| | Type | [AttributeValueType](http://support.profisee.com/wikis/profiseeplatform/attributevaluetype_enumeration) | An enumeration that identifies the Profisee-specific data type associated with this Attribute value. |
| | DoShowTime | bool | An indicator to clients that the time element of a **DateTime** attribute is relevant. This also implies that the associated value is sensitive to the time zone and should be adjusted when displayed to a user. **NOTE:** This field is relevant only when the **Type** property is set to **DateTime (3)**. |
| \* | IsMultiLevel | bool | Indicates if this Attribute is from a related entity accessed via the associated **MultiLevelContext** path. |
| | MultiLevelContext | [MultiLevelContext](http://support.profisee.com/wikis/profiseeplatform/multilevelcontext_type) | A type that describes the relationship path to this Attribute from the entity associated with the Member object that contains this Attribute in its **Attributes** collection. |
| | ValidationStatus | [ValidationStatus](http://support.profisee.com/wikis/profiseeplatform/validationstatus_enumeration) | Indicates the validation status of this Attribute associated with its containing [Member](http://support.profisee.com/wikis/profiseeplatform/member_data_type). |
| | HasRuleDefined | bool | Indicates whether or not the attribute has an associated Data Quality Rule. |
| | ValidationRuleClauseId | Nullable<int> | The internal ID associated with the Data Quality Rule clause that failed if the **ValidationStatus** is set to **ValidationFailed**. If this value is **null**, then either (a) there are no rules for this attribute, or (b) all of the rules have passed. |
| | TransactionAnnotation | string | A text annotation of a change made for this specific attribute. **NOTE:** This property is obsolete and should not be used or referenced. It is an artifact used for legacy Microsoft Master Data Services (MDS) support is not relevant in a Profisee Platform model. |

\* *Getter only*

### Remarks

The **Attribute** class represents the value of an attribute (i.e. a column) associated with a [Member](http://support.profisee.com/wikis/profiseeplatform/member_data_type) object (i.e. a member record) when read from or written to the associated entity.

When a [Member](http://support.profisee.com/wikis/profiseeplatform/member_data_type) or collection of members is read from the server, the values of the requested attributes are returned in the member record's **Attributes** collection. Each element of the collection information about the value associated with that specific Attribute.

The **Value** property of the **Attribute** class contains an object that represents the value of the attribute for that record in the entity. The value can be **null** if the record contains no value for the attribute in the database. The type of object in the **Value** property depends on the **Type** enumeration associated with the **Attribute**.

The following table specifies the object type based on the **Type** property specified:

| | |
| --- | --- |
| **Type Property** | **Underlying C# Value Type** |
| String (1) | string |
| Number (2) | double |
| DateTime (3) | DateTime |
| Domain (4) | MemberIdentifier |
| File (5) | N/A |

### See Also

- [AttributeValueType](https://support.profisee.com/wikis/profiseeplatform/AttributeValueType_Enumeration)
- [Identifier](https://support.profisee.com/wikis/profiseeplatform/identifier_type)
- [MaestroIdentifier](https://support.profisee.com/wikis/profiseeplatform/maestroidentifier_type)
- [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type)
- [MemberIdentifier](https://support.profisee.com/wikis/profiseeplatform/memberidentifier_type)
- [MultiValueContext](https://support.profisee.com/wikis/profiseeplatform/multilevelcontext_type)
- [ValidationStatus](https://support.profisee.com/wikis/profiseeplatform/validationstatus_enumeration)