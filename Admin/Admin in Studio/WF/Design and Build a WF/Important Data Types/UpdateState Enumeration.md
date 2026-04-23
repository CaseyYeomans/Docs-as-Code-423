# UpdateState Enumeration

The **UpdateState** enumeration appears in data and metadata artifact records and is used to indicate how the server should process the record when it is published to the server in various data and metadata publishing operations.

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts

### Properties

| | |
| --- | --- |
| **Enumeration Value** | **Description** |
| Auto=0 | The server determines whether to add or update depending on the specification of the associated Identifier. If this record represents an existing record, an update is performed. If the record identifies a new record, an add (insert) is performed. |
| Unchanged=1 | On a read, this is the default setting which indicates that the associated record or artifact has not been changed by the client. |
| Add=2 | Set by the client to indicate the data or artifact record is to be added to its associated repository on the server. |
| Modified=3 | Set by the client to indicate the data or artifact record is to be updated in its associated repository. |
| Delete=4 | Set by the client to indicate the data or artifact record should be deleted from its associated repository. |

### Remarks

All metadata artifacts within the Profisee data contracts contain a reference to the **UpdateState,** which allows clients to either explicitly specify the intent of a save operation or to allow the server to infer it using the **Auto** setting. In addition, the [Member](http://support.profisee.com/wikis/profiseeplatform/member_data_type) object also contains a reference to the **UpdateState** enumeration. This is leveraged primarily by survivorship and does not need to be explicitly set by clients updating data through the various create and update operations.

### See Also

- [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type)