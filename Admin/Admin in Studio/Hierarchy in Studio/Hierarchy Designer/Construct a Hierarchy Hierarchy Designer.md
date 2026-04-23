# Construct a Hierarchy Using the Hierarchy Designer

Build basic hierarchical structures using the Hierarchy Designer. DBAs must be [extended to a Relationship](https://support.profisee.com/wikis/profiseeplatform/extend_to_relationship_overview) before they can be used to build a hierarchy. You can leverage existing attribute relationships or build new ones as you create a hierarchy. You can also extend DBAs to relationships using [Advanced Modeling](https://support.profisee.com/wikis/profiseeplatform/advanced_modeling_overview).

## Create and Name the Hierarchy

1. Navigate to Administration | Hierarchies.
2. Click **New**.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i7eb41d4e9e93928d.png)
3. The Hierarchy Designer Panel opens. Enter a name for the hierarchy in the **Name** free-text field. The name is echoed as the root node of the hierarchy tree.

The examples below show a parent/child Relationship using available relationships in the hierarchy, and a recursive relationship built using new relationships created in the Hierarchy Designer. Parent, child, and recursive Relationships can be created using either method, provided required DBAs are available.

## Create a Basic Parent/Child Relationship

Available relationship structures, consisting of a parent and a child, display in the right-hand side of the panel. To create a basic parent/child relationship:

1. Click the checkbox to select the desired relationship. The hierarchy display in the left panel changes to reflect the new relationship.
2. Repeat this process, building the hierarchy either from the top down or the bottom up, until all desired levels are added.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i9f62dd54e8fd509c.png)

## Create a Recursive Relationship

A recursive relationship makes a parent member a parent of itself. There are a number of use cases for this type of relationship, two of which are described in the [Hierarchy Overview](https://support.profisee.com/wikis/profiseeplatform/hierarchies_overview).

To create a recursive relationship in the Hierarchy Designer:

1. Select the top-level member you want to update with a recursive relationship. Double-click to open the design panel.
2. In the Relationships tab, click **New**.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i2ff349389640b36a.png)
3. Select **Recursive Relationship** from the drop-down menu. The Relationship Designer opens.
4. Click the Parent Relationship Card control to activate it.
5. Select the desired entity. The [Predicate](https://support.profisee.com/wikis/profiseeplatform/predicates_in_relationship_design) auto-populates with the "is parent of" value.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i431b61f04e897b34.png)
6. Click the Child Relationship Card control to activate it.

The selected parent entity is available from the drop-down menu.
7. Select the related attribute from the drop-down menu.

The Predicate auto-populates with the "is child of" value.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-ib61d0b359198ca55.png)
8. Click **Save**.

The new relationship displays in the **Relationships** tab.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i3247b4a8560be846.png)

In the Hierarchy Definition pane, you will see folder icons representing [virtual nodes](https://support.profisee.com/wikis/profiseeplatform/predicates_in_relationship_design). The virtual nodes will only display if one entity has 2 relationships (one as the parent in a parent child relationship and another as a recursive relationship).

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i1302320e08b759f7.png)

Recursive relationships can only be built from a top-level node. Recursive relationships cannot be created using child nodes.

## See Also

[Hierarchy Designer Overview](https://support.profisee.com/wikis/profiseeplatform/hierarchy_designer_overview)

[Defining Node Properties in the Hierarchy Designer](https://support.profisee.com/wikis/profiseeplatform/define_node_properties_in_the_hierarchy_designer)

[Virtual Nodes](https://support.profisee.com/wikis/profiseeplatform/virtual_nodes)