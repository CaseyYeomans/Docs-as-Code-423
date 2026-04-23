# Identifier Type

### Summary

The **Identifier** type provides underlying base data type used for identifying all metadata and data artifacts within a Profisee Platform instance.

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts.MasterDataServices

### Properties

| | | |
| --- | --- | --- |
| **Property Name** | **Data Type** | **Description** |
| Id | Guid | A Globally-Unique Identifier (GUID) associated with this member in the Entity. |
| InternalId | int | The Profisee instance-specific ID (surrogate key) for this Entity member in this platform instance. |
| Name | string | The name given to this member in the associated Entity. |
| IsReferenceValid | bool | Indicates if the associated Id is valid. This is only used for metadata identifiers (e.g. MaestroIdentifier) and is not used for MemberIdentifier instances. |
| IsEmpty | bool | Indicates if this Identifier is semantically null (empty). |

### Remarks

The **Identifier** type contains all of the identifying properties for all metadata and data artifacts within a Profisee Platform instance. Every artifact (data and metadata) has a **Name**, an instance-specific **InternalId**, and a globally-unique **Id** (**Guid**). The globally-unique **Id** values are used when moving metadata between instances of the Profisee Platform.

### See Also

- [MaestroIdentifier](https://support.profisee.com/wikis/profiseeplatform/maestroidentifier_type)
- [MemberIdentifier](https://support.profisee.com/wikis/profiseeplatform/memberidentifier_type)
- [ModelContextIdentifier](https://support.profisee.com/wikis/profiseeplatform/modelcontextidentifier_type)