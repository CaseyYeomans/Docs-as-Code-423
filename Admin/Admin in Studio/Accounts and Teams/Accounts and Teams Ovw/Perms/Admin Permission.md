# Using the Administration Permission

The Entity Administration permission is designed to allow [Accounts](https://support.profisee.com/wikis/profiseeplatform/accounts_overview) and [Teams](https://support.profisee.com/wikis/profiseeplatform/teams_overview) with the permission to have full access to either a single entity or to all entities in the model. When combined with certain Administration Roles, it also provides additional functional permissions, such as the ability to assign permissions to an entity. Accounts with the Entity Administration permission assignment are referred to as Entity Administrators.

The following Administrator Roles are limited in scope to only those entities where the account is an Entity Administrator.

- Address Verification Administrator
- Batch Integration Administrator
- Event Administrator
- Matching and Survivorship Administrator
- Permissions Administrator

When the Entity Administration permission is assigned, attribute permissions and filter permissions at lower levels cannot be assigned

## Scenarios

### Assigning Administration at the Entities Folder

The Administration permission can be granted at the Entities folder to give Admin permission to all entities.

Accounts and teams with Administration permission at the entities level receive the following permissions in the model:

- Admin permission is implicitly assigned to all entities in the model

This displays as "Everything" in the table of explicit permission assignments on the Permissions tab.
- Other prior permission assignments in the model are replaced with the Admin permission
- Any Read or Update filters are removed for all entities

### Assigning Administration at the Single Entity Level

The Administration permission can be granted to a single entity. This allows an Account or Team to have full access to the data and perform administrative actions on the entity based on their assigned administrator roles.

Accounts and Teams with Administration permission at the single entity level receive the following permissions for the entity:

- Admin permission is explicitly assigned for the entity
- Update permission is implicitly assigned to all attributes in the entity
- Any Read or Update filters in the entity are removed