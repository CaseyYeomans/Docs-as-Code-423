# PermissionType Enumeration

The **PermissionType** enumeration is the legacy MDS attribute-level security indicator associated with member record attributes.

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts.MasterDataServices

### Properties

| | |
| --- | --- |
| **Enumeration Name** | **Description** |
| Unknown=0 | The default value; not used when metadata is properly defined on the server. |
| NotSpecified=1 | No explicit permission has been specified for the associated attribute. Permissions are inferred from the associated entity. |
| Update=2 | The current user has been granted update rights to the associated attribute. |
| ReadOnly=3 | The current user has been granted read-only rights to the associated attribute. |
| Delete=4 | The user has been granted delete (clearing) rights to the associated attribute. |

### Remarks

The **PermissionType** enumeration is a legacy MDS value to which the Profisee Platform data services translates its associated [SecurityPermissionType](http://support.profisee.com/wikis/profiseeplatform/securitypermissiontype_enumeration) enumeration. This is done for backward compatibility purposes. The most accurate information regarding the for a given attribute should be obtained from the **ProfiseePermission** property of the associated [MetadataAttribute](http://support.profisee.com/wikis/profiseeplatform/metadataattribute_type) class.

### See Also

- [MetadataAttribute Type](https://support.profisee.com/wikis/profiseeplatform/metadataattribute_type)
- [SecurityPermissionType Enumeration](https://support.profisee.com/wikis/profiseeplatform/securitypermissiontype_enumeration)