# SecurityPermissionType Enumeration

The **SecurityPermissionType** enumeration specifies the permissions granted to a specific user that is being represented by the connected client for the associated artifact.

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts

### Properties

| | |
| --- | --- |
| **Enumeration Value** | **Description** |
| Enumeration Value | The user has no access to the associated attribute. |
| NoAccess=0 | The user has read permission to the associated attribute, member, or entity. |
| Update=2 | The user has update permission to the associated attribute, member, or entity. |
| UpdateCreate=3 | The user has permissions to create and update members in the associated entity. |
| UpdateCreateDelete=4 | The user has permission to create, update, and delete members in the associated entity. |
| Administration=5 | The user is specified as an Administrator of the specified entity. |

### Remarks

**Entity** and **MetadataAttribute** classes have associated a **ProfiseePermission** property that is of type **SecurityPermissionType**. This field indicates the permissions that have been granted to the user that happens to be reading data associated with the entity or attribute.

Permissions granted at the entity level cascade to the attribute level unless overridden at the attribute level. If the user is granted administrative rights to the entity through his or her Team or AD group assignment or explicitly at the individual account level, then the **ProfiseePermission** will be set to **Administration (5)**.

### See Also

- [MetadataAttribute Type](https://support.profisee.com/wikis/profiseeplatform/metadataattribute_type)