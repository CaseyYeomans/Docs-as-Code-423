# Predicates in Relationship Design

Each role in a relationship contains a Predicate property. The Predicate describes the manner in which the subject entity in the role relates to the object entity. For example, in the relationship between the HmProduct and HmProductSubcategory entities, HmProduct is the subject entity while HmProductSubcategory is the object entity.

## View Predicate Properties

To view this in the Relationship Designer:

1. Select the target entity from the Relationship folder in Advanced Modeling. Right-click, and select **Edit** from the drop-down menu.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-ib1c2a4715f1000ba.png)

2. The Relationship Designer opens in Edit mode. The images below show the Predicate displays for the parent and child cards.

| | |
| --- | --- |
| | |

Each role type has a default predicate that is applied each time a new relationship role is created. The default predicates for Parent/Child roles are:

| Role Type | Default Predicate |
| --- | --- |
| Parent | is parent of |
| Child | is child of |

## Change the Default Predicate Label

You can change the default predicate label to a more appropriate description for the subject relationship and entities.

To change the predicate:

1. Click the role card for the target entity. When the card is activated, the Predicate free-text field is editable.
2. Enter the desired name.
3. Click **Save**.
4. Click **Publish to Server**.

The predicate value has no effect on relationship and hierarchy operations; it is merely used to help better understand how the entities in a relationship relate to one another.

## See Also

[Extend DBA to Relationship in Advanced Modeling](https://support.profisee.com/wikis/profiseeplatform/extend_dba_to_relationship_in_advanced_modeling)

[Construct a Hierarchy Using the Hierarchy Designer](https://support.profisee.com/wikis/profiseeplatform/construct_a_hierarchy_using_the_hierarchy_designer)