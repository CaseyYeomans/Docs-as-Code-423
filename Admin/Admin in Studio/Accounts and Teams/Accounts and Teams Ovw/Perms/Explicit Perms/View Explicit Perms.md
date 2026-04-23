# View Explicit Permissions

View permission assignments from the Permissions tab under the [account](https://support.profisee.com/wikis/profiseeplatform/accounts_overview) or [Team](https://support.profisee.com/wikis/profiseeplatform/teams_overview) edit panel. An explicit assignment is made specifically for that account or team. Effective account permissions may differ.

## For accounts

View Explicit Permissions for an account:

1. Under Administration, click **Accounts and Teams**.
2. Click **Accounts**.
3. Select an account in the list.

The Account edit panel opens.
4. Click the **Permissions** tab.

The Explicit Permission assignments for the selected account display.

## For Teams

View Explicit Permissions for a team:

1. Under Administration, click **Accounts and Teams**.
2. Click **Teams**.
3. Select a team in the list.

The Team edit panel opens.
4. Click the **Permissions** tab.

The Explicit Permission assignments for the selected team display.

## Displayed Explicit Permission Information

| | |
| --- | --- |
| **Column Name** | **Description** |
| **Object:** | The name of the entity or attribute where the permission is assigned |
| **Type** | The type of object permission. Type can be: - Entity All Account has permission to all attributes in the entity and any attributes added in the future - Entity Partial Account has permission to some of the attributes in the entity. Permission will not automatically be granted to new attributes added in the future. - Attribute Account has permission to the attribute - Filter Account permissions for an entity are modified by a filter to limit the members that may be seen or updated. - Everything Account has permission to all entities in the model and any entities added in the future |
| **Permission** | The name of the permission assigned to the object |
| **Details** | Additional information about the permission assignment. The filter expression is included here for filter permissions. For more information, see [Understanding filter-based permissions](https://support.profisee.com/wikis/profiseeplatform/using_filter_permissions). |

- Broader permissions explicitly granted at higher levels in the model are inherited by lower levels for both accounts and teams, unless overridden at the lower levels.
- Entity level permissions allow inheritance at the same access level to new attributes when they are created, unless there are individual attribute assignments. When individual attribute assignments exist, permissions to new attributes must be explicitly assigned.