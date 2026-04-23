# Using Entity Permissions

**Entity Permissions** are permissions associated with entity model objects. Entity Permissions may be thought of as table-level permissions.

Use Entity Permissions when you do not need to vary the permissions by attribute, or when you want most attributes to default to a common permission level. Generally, you should set Entity Permissions first before [Attribute Permissions](https://support.profisee.com/wikis/profiseeplatform/use_attribute_permissions) as this will set the default permission for all attributes that you do not set directly.

Change Entity Permissions to update attribute permissions through inheritance.

- **Update, Update Create**, or **Update Create Delete** at the entity level results in **Update** for the attributes
- **Read** at the entity level results in **Read** for the attributes
- **No access** at the entity level results in **No Access** for the attributes
- **Administration** at the entity level results in **Update** for the attributes

## Scenarios

### Changing an Entity Permission when explicit Attribute Permissions exist

Any change in entity permission, other than changing to a variation of Update, will discard attribute-level permissions and reapply inherited (default) permissions at the attribute level. This is helpful when you need to change the default permission assigned to the majority of attributes and then override a select few attributes by exception. For example, if you want to assign mostly Update permission with only a few attributes being Read-only or No Access, then assign Update at the Entity level first, then change the selected attributes to another permission.