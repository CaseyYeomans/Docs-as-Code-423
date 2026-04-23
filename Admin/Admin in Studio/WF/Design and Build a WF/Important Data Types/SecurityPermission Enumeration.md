# SecurityPermission Enumeration

The **SecurityPermission** enumeration specifies the user's access to the [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type) object with which it is associated.

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts.MasterDataServices

### Properties

| | |
| --- | --- |
| **Enumeration Name** | **Description** |
| NotSpecified=0 | The default value and should generally not be used when data is read from the server. |
| Deny=1 | The current user does not have rights to the associated Member record. |
| Read=1 | The current user has read-only rights to the associated Member record. |
| Update=2 | The current user has update rights to the associated Member record. |
| Inferred=3 | Not used. **NOTE**: This is a legacy Microsoft Master Data Services (MDS) value and is not used within the Profisee Platform. |
| Access=4 | Not used. **NOTE**: This is a legacy Microsoft Master Data Services (MDS) value and is not used within the Profisee Platform. |

### Remarks

The **SecurityPermission** enumeration is a legacy MDS value to which the Profisee Platform data services translates its associated [SecurityPermissionType](http://support.profisee.com/wikis/profiseeplatform/securitypermissiontype_enumeration) enumeration. This is done for backward compatibility purposes. The most accurate information regarding the for a given attribute should be obtained from the **ProfiseePermission** property of the associated [MetadataAttribute](http://support.profisee.com/wikis/profiseeplatform/metadataattribute_type) class.

### See Also

- [Member Type](https://support.profisee.com/wikis/profiseeplatform/member_data_type)
- [MetadataAttribute Type](https://support.profisee.com/wikis/profiseeplatform/metadataattribute_type)
- [SecurityPermissionType Enumeration](https://support.profisee.com/wikis/profiseeplatform/securitypermissiontype_enumeration)