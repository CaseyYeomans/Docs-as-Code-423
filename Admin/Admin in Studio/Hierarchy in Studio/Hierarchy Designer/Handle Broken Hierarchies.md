# Handle Broken Hierarchies

A hierarchy configuration can be broken when changes in the data model invalidate the underlying relationship. Examples include:

- Deleting a relationship used in the hierarchy
- Deleting an entity from a hierarchy relationship

A hierarchy configuration is validated when it is loaded by the server. This happens when:

- Hierarchy metadata is cached by the server during start-up
- Hierarchies are requested by a client (such as FastApps Portal or Studio)

When the server determines that an underlying model change has broken a hierarchy, that hierarchy is flagged in the Hierarchies tab as defective.

The defective hierarchy must be deleted and recreated.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i8302283ba56714d1.png)

If you attempt to open the defective hierarchy, a message prompt displays. Click Yes to delete the defective hierarchy.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i28ed38cc0a51f7e.png)

The hierarchy is deleted and can now be recreated.

## See Also

[Hierarchies Overview](https://support.profisee.com/wikis/profiseeplatform/hierarchies_overview)

[Construct a Hierarchy Using the Hierarchy Designer](https://support.profisee.com/wikis/profiseeplatform/construct_a_hierarchy_using_the_hierarchy_designer)

[Extend DBA to Relationship in Advanced Modeling](https://support.profisee.com/wikis/profiseeplatform/extend_dba_to_relationship_in_advanced_modeling)