# Virtual Nodes

The FastApps Studio Hierarchy Designer allows you to build recursive hierarchies that include non-recursive children of the selected subject node, so you can easily traverse hierarchies containing recursive relationships. The most common example is an entity that has a recursive relationship as well as another non-recursive child relationship.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i91c544d3c8752908.png)

When a hierarchy configuration includes a recursive relationship along with a non-recursive child relationship below the recursive node, virtual nodes are introduced to allow the recursive children to be separated from the non-recursive children when navigating the hierarchy.

When a hierarchy has both recursive and non-recursive children, the Hierarchy Designer creates virtual nodes representing containers for the individual child types that fall physically below the selected node in the relationship.

These containers are placeholders and do not physically exist within the data itself. Virtual nodes cannot be added, updated, moved, or deleted during stewardship operations. However, children can be added to a virtual node. This effectively adds a new child of the specified virtual node's entity type to the subject recursive node during stewardship. Virtual nodes help you visualize and interact with both recursive and non-recursive children.

## See Also

[Hierarchy Designer Overview](https://support.profisee.com/wikis/profiseeplatform/hierarchy_designer_overview)

[Construct a Hierarchy Using the Hierarchy Designer](https://support.profisee.com/wikis/profiseeplatform/construct_a_hierarchy_using_the_hierarchy_designer)

[Defining Node Properties in the Hierarchy Designer](https://support.profisee.com/wikis/profiseeplatform/define_node_properties_in_the_hierarchy_designer)