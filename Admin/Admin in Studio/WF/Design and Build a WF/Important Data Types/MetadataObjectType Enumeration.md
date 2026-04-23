# MetadataObjectType Enumeration

The **MetaDataObjectType** enumeration allows various metadata artifacts within the platform to explicitly declare their type by implementing the **IMetadataObject** interface which a **MetadataObjectType** property of this enumeration type.

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts

### Properties

| | |
| --- | --- |
| **Enumeration Name** | **Description** |
| Unknown=0 | The default value and should not be present for well-defined metadata objects. |
| AttributeGroup=1 | Identifies an **AttributeGroup** object. |
| DeriviedHierarchy=2 | **Obsolete** - Identifies a **DerivedHierarchy** object. |
| Entity=3 | Identifies an **Entity** artifact. |
| ExplicitHierarchy=4 | **Obsolete** - Identifies an **ExplicitHierarchy** artifact. |
| MetadataAttribute=5 | Identifies a [MetadataAttribute](http://support.profisee.com/wikis/profiseeplatform/metadataattribute_type) artifact. |
| Model=6 | Identifies a **Model** artifact. |
| Version=7 | Identifies a **Version** artifact. |
| VerisonFlag=8 | **Obsolete** - Identifies a **VersionFlag** artifact. |
| AuditAttribute=9 | Identifies an **AuditAttribute** artifact. |
| MaestroMetadataGroup=10 | Identifies a **MaestroMetadataGroup** artifact. |
| Relationship=11 | Identifies a **Relationship** artifact. |

### Remarks

The MetadataObjectType enumeration allows each model metadata artifact to explicitly declare its object type through its implementation of the IMetadataObject interface.

### See Also

- [MetadataAttribute Type](https://support.profisee.com/wikis/profiseeplatform/metadataattribute_type)