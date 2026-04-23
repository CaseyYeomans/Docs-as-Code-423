# MaestroIdentifier Type

The **MaestroIdentifier** type provides underlying base data type used for identifying all Profisee-specific metadata and artifacts within a Profisee Platform instance.

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts

### Properties

| | | | | |
| --- | --- | --- | --- | --- |
| | **Property Name** | | **Data Type** | **Description** |
| | | Id | Guid | A Globally-Unique Identifier (GUID) associated with this member in the entity. |
| | | InternalId | int | The Profisee instance-specific ID (surrogate key) for this Entity member in this platform instance. |
| | | Name | string | The name given to this member in the associated Entity. |
| | | IsReferenceValid | bool | Indicates if the associated Id is valid. This is only used for metadata identifiers (e.g. MaestroIdentifier) and is not used for MemberIdentifier instances. |
| \* | | IsBlank | bool | Indicates if this Identifier is semantically null (empty). |

\* *Getter only*

### Remarks

The **MaestroIdentifier** type contains all the identifying properties for all metadata and data artifacts within a Profisee Platform instance. Every artifact (data and metadata) has a **Name**, an instance-specific **InternalId**, and a globally-unique **Id** (**Guid**). The globally-unique **Id** values are used when moving metadata between instances of the Profisee Platform. The **MaestroIdentifier** is essentially the same as the [Identifier](http://support.profisee.com/wikis/profiseeplatform/identifier_type) type which originated from the Microsoft Master Data Services (MDS) data contracts.

### See Also

- [Identifier Type](https://support.profisee.com/wikis/profiseeplatform/identifier_type)