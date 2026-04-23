# Permissions Overview

Assign data permissions to accounts at the entity and attribute level -- the columns of the database table. Use filter permissions to control data members at the row level.

Attribute filter permissions restrict access to member data at the row level. Each entity includes two filters:

- **Read**

Limits the members an account can see based on the filter criteria
- **Update**

Limits the members an account can create, change and delete based on the filter criteria

Simultaneous Read and Update permission filter assignments are possible, allowing control over the data members an account can see and those the account can update, create, or delete.

Right-clicking the Read or Update filters opens a menu with three options:

- **Edit** (creates a filter)

Accounts can only access data members matching the criteria for this filter for this permission (Read or Update, or a combination of the two)
- **Clear**

Removes any currently applied filters
- **All Members** (the default)

Allows access to all data members in the entity

Filters are additive (with OR logic) when an account belongs to multiple teams having a filter permission assignment. Apply filter permissions to an account either through explicit assignment or through team membership.

Attribute permission filters can include any criteria supported in an entity grid filter, including multiple lines and parent attributes. For more information on constructing filters, see Building an entity grid filter, Multi-line entity grid filters and Filtering using parent attributes.

## Attribute Filter Permission Usage Example

Filter Permissions offer finer control over data access for accounts and teams. Consider an organization that produces bicycles. The data steward in this example should be able to edit all attribute data in the Product entity, but only for the blue bicycles.

This data steward is assigned the **Update Create Delete** permission on the Product entity. The following filter permission is applied to the Color attribute (a domain-based attribute) in the Product entity:

**Update Filter {[Color].[Code] = 'BLU'}**

A sample of unfiltered data looks like this:

| Name | Code | Color | Gender | Style | Cost |
| --- | --- | --- | --- | --- | --- |
| Mountain-101 | M101 | Blue | M | Mountain | 500.00 |
| Racing-101 | R101 | Silver | M | Racing | 2000.00 |
| Mountain-102 | M102 | Blue | W | Mountain | 650.00 |
| Touring-505 | T505 | Blue | W | Touring | 200.00 |
| Mountain-103 | M103 | Black | M | Mountain | 450.00 |
| Touring-501 | T501 | Red | W | Touring | 350.00 |

But the data steward with the update filter permission assignment only sees, and may update, this:

| Name | Code | Color | Gender | Style | Cost |
| --- | --- | --- | --- | --- | --- |
| Mountain-101 | M101 | Blue | M | Mountain | 500.00 |
| Mountain-102 | M102 | Blue | W | Mountain | 650.00 |
| Touring-505 | T505 | Blue | W | Touring | 200.00 |

Although the data steward could add blue bicycles, he could not add a yellow bicycle. Accounts cannot create members which their permissions prevent them from accessing.

## Additive Filters

Filters are combined using a logical OR operation when an account's access is affected by multiple filters for the same entity. If this same account was part of a team where the Product entity had this filter applied:

**Read Filter {[Color].[Code] = 'RED**

The account would see members where the color was red or where the color was blue.

| Name | Code | Color | Gender | Style | Cost |
| --- | --- | --- | --- | --- | --- |
| Mountain-101 | M101 | Blue | M | Mountain | 500.00 |
| Mountain-102 | M102 | Blue | W | Mountain | 650.00 |
| Touring-505 | T505 | Blue | W | Touring | 200.00 |
| Touring-501 | T501 | Red | W | Touring | 350.00 |

If the account became a member of another team where the Read filter for the entity where Color was set to **All Members**, then the account would see all members. The All Members filter would take precedence over the Red and Blue filters conveyed through team membership. Broader permissions always take precedence over more restrictive permissions.

The Permissions Administrator role is required to assign permissions.