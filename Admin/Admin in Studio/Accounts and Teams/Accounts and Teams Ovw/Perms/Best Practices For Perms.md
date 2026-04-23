# Best Practices For Permissions

- Apply permissions broadly where possible (i.e., All Entities or Entity Permissions) to reduce permission maintenance required by explicitly assigned Attribute Permissions. You may still override Entity Permissions at the attribute level by exception. See [Inherited Permissions](https://support.profisee.com/wikis/profiseeplatform/inherited_permissions) for more information.
- If you are uncertain about the outcome of a permission assignment, try it first in a test environment.

Permissions are applied right away when changes are saved for a account or team. If you want to see what a account's effective permissions will be given a combination of team and account assignments, test it first, and view the account's effective permissions to check that the assignment fulfills your requirements.
- When possible, assign permissions to teams instead of single accounts.

It is easier and more efficient to administer permissions through teams than it is to do so for individual accounts.