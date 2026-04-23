# AuditInfo Type

The **AuditInfo** type is used to identify who was responsible for creating and updating data and metadata artifacts within the Profisee Platform.

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts.MasterDataServices

### Properties

| | | |
| --- | --- | --- |
| **Property Name** | **Data Type** | **Description** |
| CreatedDateTime | DateTime | The date and time the data record or artifact was created. |
| CreatedUserId | [Identifier](https://support.profisee.com/wikis/profiseeplatform/identifier_type) | Identifies the user responsible for the data record or artifact creation. |
| UpdatedDateTime | DateTime | The date and time the data record or artifact was last updated. |
| UpdatedUserId | [Identifier](https://support.profisee.com/wikis/profiseeplatform/identifier_type) | Identifies the user responsible for the last update to the data record or artifact. |
| CreatedVersionId | [Identifier](https://support.profisee.com/wikis/profiseeplatform/identifier_type) | Identifies the version of data in which the member was created. **NOTE**: This property is a legacy artifact of Microsoft MDS support and is obsolete and no longer in use. |
| UpdatedVersionId | [Identifier](https://support.profisee.com/wikis/profiseeplatform/identifier_type) | Identifies the version of data in which the member was last updated. **NOTE**: This property is a legacy artifact of Microsoft MDS support and is obsolete and no longer in use. |

### Remarks

The **AuditInfo** type is used to identify who was responsible for creating and updating data and metadata artifacts within the Profisee Platform. The information in this type can be modified by a client, but will be ignored during the data or artifact creation process as the dates and times are computed on the server as part of the data access operation. This information is stored along with the data and metadata within the various data and artifact tables. Dates and times are stored as UTC but are converted to the client time zone as part of the serialization process.

### See Also

- [Identifier Type](https://support.profisee.com/wikis/profiseeplatform/identifier_type)