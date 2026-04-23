# ModelContextIdentifier Type

The **ModelContextIdentifier** inherits from Identifier and adds the identifier for the specific Model to which a given artifact (e.g. an Entity) belongs.

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts.MasterDataServices

### Properties

| | | |
| --- | --- | --- |
| **Property Name** | **Data Type** | **Description** |
| ModelId | [Identifier](https://support.profisee.com/wikis/profiseeplatform/identifier_type) | Identifies the model **InternalId**, globally **Id**, and **Name**. |

### Remarks

Artifacts that belong to a specific model use the **ModelContextIdentifier** to identify themselves as well as the Model to which they belong. For example, an **EntityContextIdentifier** extends the **ModelContextIdentifier** thus linking the associated Entity to the Model specified by the **ModelId** property.

### See Also

- [I](https://support.profisee.com/wikis/profiseeplatform/modelcontextidentifier_type)[dentifier](https://support.profisee.com/wikis/profiseeplatform/identifier_type)