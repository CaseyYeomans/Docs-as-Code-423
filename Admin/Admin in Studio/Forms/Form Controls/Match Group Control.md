# Match Group Control

## Configuration

The Match Group control displays a match group and allows users to perform management tasks on the group.

| Property | Property Option | Description |
| --- | --- | --- |
| Context | Matching Strategy | The matching strategy to use in the control. Only strategies that use the same entity as the form display in the list. |

## Permissions

Permissions behave differently for the Match Group control in a form than they do for Matching Results in the Profisee application. Users must have minimum permissions to attributes as outlined in the following table.

| Control Attribute | Permissions required to view results | Permissions required to perform management tasks (approve and reject) |
| --- | --- | --- |
| Match group ID | Read-only | Update |
| Match score | Read-only | Update |
| Match status | Read-only | Update |
| Record source | Read-only | Update |
| Match member | Read-only | Update |
| Strategy step | Read-only | Update |
| Match date | Read-only | Update |
| Match user | Read-only | Update |
| Multi group | Read-only | Update |
| Matching attributes | Read-only | Read-only |
| Master | Read-only (when survivorship is included) | Update (when survivorship is included) |
| Approved Count | Read-only (when survivorship is included) | Update (when survivorship is included) |
| Proposed Count | Read-only (when survivorship is included) | Update (when survivorship is included) |
| Survivorship attributes | Read-only (when survivorship is included) | Update (when survivorship is included) |