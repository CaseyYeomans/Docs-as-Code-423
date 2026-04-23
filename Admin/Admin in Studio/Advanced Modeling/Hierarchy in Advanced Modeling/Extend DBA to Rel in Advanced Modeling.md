# Extend  DBA to Relationship in Advanced Modeling

While the [Hierarchy Designer](https://support.profisee.com/wikis/profiseeplatform/hierarchy_designer_overview) is the primary hierarchy building tool in Profisee FastApps Studio, you can also construct hierarchies using the visualizer tree in Advanced Modeling. DBAs must be [extended to a Relationship](https://support.profisee.com/wikis/profiseeplatform/extend_to_relationship_overview) before they can be used to build a hierarchy. There are two ways to create a Relationship in Advanced Modeling: From an attribute, or from the Relationships folder.

### Extend to Relationship From an Attribute

To extend a DBA to a relationship directly from an attribute:

1. Click the DBA you want to update in the visualizer tree.
2. Right-click and select **Extend to Relationship**.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i1b37b5faab698f88.png)

3. The Relationship Designer opens. Click the Parent Relationship Card control to activate it.
4. The entity auto-populates with the correct value, as you are working from the entity context. The [Predicate](https://support.profisee.com/wikis/profiseeplatform/predicates_in_relationship_design) auto-populates with the "is parent of" value.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-ia6ef5723f3cd9b23.png)

5. Select the Child Relationship Card control to activate it.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-icb65d7d072770289.png)

The parent entity and attribute are auto-populated.The Predicate auto-populates with the "is child of" value.
6. Click **Save**.

The new Relationship appears in the Relationships folder.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-if5a0efaf157bf11.png)

Parent/child Relationships appear in the folder for both entities.

Because a non-recursive DBA was selected, the example above results in the creation of a parent/child Relationship. Recursive relationships are built in the same manner using a recursive DBA. Refer to [Construct a Hierarchy Using the Hierarchy Designer](https://support.profisee.com/wikis/profiseeplatform/construct_a_hierarchy_using_the_hierarchy_designer) for more information about creating recursive Relationships.

### Extend to Relationship from the Relationships Folder

To extend a DBA to a Relationship from the Relationships folder:

1. Right-click the Relationships folder and select **Create**.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-id09c984214941e2d.png)

2. Select the type of relationship (Child, Parent, or Recursive) you want to create.
3. The Relationship Designer opens, as pictured in the previous section.

Depending on your selection, some fields in either the Parent or Child Relationship Card controls are auto-populated with any values applicable for that context. Select the remaining values from the drop-down menus.
4. Click **Save**.

The new relationship appears in the Relationships folder.