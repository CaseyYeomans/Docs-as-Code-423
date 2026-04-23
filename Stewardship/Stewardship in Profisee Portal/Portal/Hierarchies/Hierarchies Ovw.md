# Hierarchies Overview

Hierarchies are an arrangement of entity relationships into a tree structure that supports the ability to visualize, navigate, and process data in those entities in a top-down or bottom-up manner. Profisee's approach to hierarchies is based on entity relationships, which eliminates the need for alternate member types (consolidated vs. leaf). Hierarchies support a variety of use cases, including:

- Organization of records in an entity into a tree such as line management hierarchy in an employee entity
- Defining a taxonomy of entities such as products or customers
- Defining a consolidation structure such as a chart-of-accounts for use in data warehousing and reporting

Before hierarchies can be built, relationships must be created. Typically relationships are created in Advanced Modeling, but they can also be created on the fly while defining a hierarchy.

## Relationship Types

Hierarchies are based on relationships between members defined by DBA attributes. Profisee's hierarchy designer features two types of relationships:

### Parent/Child

when a Parent/Child relationship is created, the Parent and Child roles are created, with the Child entity referring to Parent entity, and the Parent entity refers to the Child entity.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-ibbb2904fcdf3290b.png)

### Recursive

In a Recursive relationship, Parent and Child are one and the same. A recursive relationship allows for an arrangement of members within a single entity into a tree structure. The entity has a relationship to itself allowing each member to refer to a different member as its associated parent. Members with an empty (NULL) relationship are considered apex members of the relationship. Common use cases for this structure include organizational charts depicting personnel reporting to multiple managers and records of financial accounts in which account data is organized arbitrarily to meet regulatory audit requirements.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-ia58d45e737da64fd.png)

## Hierarchies in Profisee

### Hierarchy Administration in FastApps Studio

Use Profisee FastAppss Studio to create, edit, and update hierarchies. See the following topics for specific instructions.

[Construct a Hierarchy Using the Hierarchy Designer](https://support.profisee.com/wikis/profiseeplatform/construct_a_hierarchy_using_the_hierarchy_designer)

[Extend DBA to Relationship Using Advanced Modeling](https://support.profisee.com/wikis/profiseeplatform/extend_dba_to_relationship_in_advanced_modeling)

### Hierarchy Stewardship in the FastApps Portal

Data stewards can accomplish the following actions with hierarchies in Portal:

- View and navigate the hierarchy
- Move a member or members to a new parent
- Search the hierarchy for a member or alternative parents
- Add members to the hierarchy
- Detach a member from the hierarchy

## See Also

[Configure the Hierarchy Control](https://support.profisee.com/wikis/profiseeplatform/configure_the_hierarchy_control) (FastApps Portal Page)

[Hierarchy Form Control](https://support.profisee.com/wikis/profiseeplatform/hierarchy_control) (Portal Form)