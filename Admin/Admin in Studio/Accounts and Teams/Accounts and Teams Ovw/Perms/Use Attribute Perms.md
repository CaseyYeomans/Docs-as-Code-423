# Use Attribute Permissions

Attribute Permissions are associated with attribute model objects. Attribute permissions may be thought of as column-level permissions.

## Use Attribute Permissions

**Attribute Permissions** are associated with attribute model objects. Attribute permissions may be thought of as column-level permissions.

Explicitly assign permissions at the attribute level when you do not want to provide access to all attributes within an entity or you want to override the default permission inherited from the Entity level.

Once attribute permissions are explicitly assigned, the system assumes you want to control attribute permissions individually, and any new attribute added to that entity will have No Access permission by default for that Account or Team.

## Implied Permissions from Domain Based Attributes

An account having Update permission to a domain based attribute is of little value without at least Read permission to the source entity (Code and Name at a minimum). I.e. the account must be able to see the list of valid choices within the domain in order to update the attribute. Therefore, the system assumes an implied Read permission on the Code and Name of the source entity for each Update permission assigned to a DBA. In this case, the system ensures that related and necessary permissions are handled for you, and you will see additional implied permissions on source entities when viewing effective permissions for the account.

## Permission to the Code Attribute

The business key or Code attribute has special behavior. You cannot remove permission to Code (i.e. a minimum of Read assignment) when permission is assigned to other attributes, as the account would not be able to reliably identify the member or row of data without this key.

The system will assign a permission to Code by default when none exists and you assign a permission directly to any other attribute within the entity.

## Permission to the Name Attribute

The system will assign a permission to Name by default when none exists and you assign a permission directly to any other attribute within the entity. However, this assumption can be overridden; you may set Name to No Access when desired.

## Filter Permission

Filter Permissions filters control optional row-level access. Accounts or teams must have the necessary minimum permission to the entity for filter permission filters to be applied.

## See Also

- [Permissions Overview](https://support.profisee.com/wikis/profiseeplatform/permissions_overview)
- [Assign Explicit Permissions](https://support.profisee.com/wikis/profiseeplatform/assign_permissions)