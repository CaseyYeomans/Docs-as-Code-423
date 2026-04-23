# Using Filter Permissions

**Filter Permissions** are permissions associated with data members within an entity. Filter Permissions may be thought of as row-level permissions.

By default, accounts receive the same permissions to all members within an entity based on their effective entity and attribute permissions. To override the default behavior at the member level and limit the data members (rows) that the account may read or update, use Filter Permissions.

Note that entity and attribute permissions (tables and columns) and filter permissions (row) intersect at the data cell level to determine the net permission to that cell. Therefore, the account must have Update permission to both the column and row to update a given data value. Similarly, the account must be able to read both the column and the row in order to view a given data value.

Keep in mind that the most permissive assignment wins when combining teams (and the direct account assignments) therefore, an account with access to all members via membership in one team will receive access to all members, regardless of filter permissions applied in another team.

## Filter Availability

Apply filters based on Account or Team Permissions at the entity level. Read and Update filters are available according to the table below:

| Entity Permission | Read Filter | Update Filter |
| --- | --- | --- |
| **None** | unavailable | unavailable |
| **Read** | available | unavailable |
| **Update** or **Update Create** or **Update Create Delete** | available | available |

## Scenarios

### Assigning a Read Permission Filter for an Entity

Assign a Read permission filter to limit the data members that may be accessed. When filter permissions are applied, the account may only read members that meet either the Read filter or the Update filter criteria.

### Assigning an Update Filter for an Entity

Assign an Update permission filter to limit the data members that may be updated or created.

When filter permissions are applied, the account may only update or create members that meet the Update filter criteria. Also the account may not save a change that will result in the member not meeting the Update filter criteria.

An account or team must have some form of Update permission to the entity before the Update permission filter can be applied.

### Permission is Changed from Update to Read at the Entity Level when an Update Permission Filter is Present

In this situation, the filter permissions are affected by the entity permission change. The Update filter is removed from the entity as it is no longer relevant.