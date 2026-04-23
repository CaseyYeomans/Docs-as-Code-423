# RecordIdentifier Type

The **RecordIdentifier** type provides the identifying properties for an individual record record within a specific Entity in a specific Profisee Platform instance.

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts.MasterDataServices

### Properties

| | | | |
| --- | --- | --- | --- |
| | **Property Name** | **Data Type** | **Description** |
| | Id | Guid | A Globally-Unique Identifier (GUID) associated with this record in the Entity. *Inherited from Identifier* |
| | InternalId | int | The Profisee instance-specific ID (surrogate key) for this Entity record in this platform instance. *Inherited from Identifier* |
| | Name | string | The name given to this record in the associated Entity. *Inherited from Identifier* |
| | IsReferenceValid | bool | Indicates if the associated Id is valid. This is only used for metadata identifiers (e.g. MaestroIdentifier) and is not used for RecordIdentifier instances. *Inherited from Identifier* |
| \* | IsEmpty | bool | Indicates if this Identifier is semantically null (empty). *Inherited from Identifier* |
| | Code | string | The unique business key associated with the record record. |
| | RecordType | RecordType | Identifies the type of record to which this **RecordIdentifier** is associated. **NOTE:** This is a legacy property and, as of version 7 of the platform, only contains a single value of Leaf(1). All other values are for backward compatibility purpose only. |
| | SystemAwareID | string | The ID of this record in an external system. **NOTE:** This value is **null** except when the record is read through any of the System Aware get operations. At this time, workflow does not support activities that read records through the System Aware operations. |
| | CodeValidationIssueClauseId | Nullable<int> | When non-**null**, this identifies the Data Quality Rule clause that has been violated for the **Code** attribute. |
| | NameValidationIssueClauseId | Nullable<int> | When non-**null**, this identifies the Data Quality Rule clause that has been violated for the **Name** attribute. |
| | CodeHasRuleDefined | Nullable<bool> | A boolean that indicates whether a Data Quality Rule exists on the **Code** attribute. |
| | NameHasRuleDefined | Nullable<bool> | A boolean that indicates whether a Data Quality Rule exists on the **Name** attribute. |
| | CodeValidationStatus | [ValidationStatus](https://support.profisee.com/wikis/profiseeplatform/validationstatus_enumeration) | Indicates the Data Quality Rule validation status of the **Code** attribute. |
| | NameValidationStatus | [ValidationStatus](https://support.profisee.com/wikis/profiseeplatform/validationstatus_enumeration) | Indicates the Data Quality Rule validation status of the **Code** attribute. |

\* *Getter only*

### Remarks

The **RecordIdentifier** type contains all of the identifying properties for a specific record record in a specific entity of a specific Profisee Platform instance. In addition to the identifying characteristics, it also provides Data Quality Rule information as pertains to the **Code** and **Name** system atttributes.

### See Also

- [Identifier](https://support.profisee.com/wikis/profiseeplatform/identifier_type)
- [Record](https://support.profisee.com/wikis/profiseeplatform/member_data_type)
- [ValidationStatus](https://support.profisee.com/wikis/profiseeplatform/validationstatus_enumeration)