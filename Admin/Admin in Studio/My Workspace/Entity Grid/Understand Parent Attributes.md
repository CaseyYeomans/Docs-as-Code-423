# Understand Parent Attributes

Parent attributes are attributes from related parent or ancestor entities. These attributes are referenced through domain-based attributes, which provide a path to the domain entity from the currently viewed entity.

For example, consider a Product entity view where Color is a DBA:

| | | | | |
| --- | --- | --- | --- | --- |
| Name | Code | Color | StandardCost | ReorderPoint |
| Mountain | 001 | BLK [Black] | 1200.00 | 800 |
| Touring | 002 | BLK [Black] | 1400.00 | 500 |
| Racing | 003 | RED [Red] | 3000.00 | 200 |
| Track | 004 | YLO [Yellow] | 1500.00 | 250 |

The Color entity, which is the domain for the Color DBA above, contains the following attributes:

| | | |
| --- | --- | --- |
| Name | Code | Type |
| Black | BLK | Neutral |
| Red | RED | Primary |
| Yellow | YLO | Primary |
| Silver | SVR | Metallic |

Using parent entities, it is possible to display the Type attribute in the Color entity in Product by referencing it through the Color DBA already in Product:

| | | | | | |
| --- | --- | --- | --- | --- | --- |
| Name | Code | Color | StandardCost | ReorderPoint | Color.Type |
| Mountain | 001 | BLK [Black] | 1200.00 | 800 | Neutral |
| Touring | 002 | BLK [Black] | 1400.00 | 500 | Neutral |
| Racing | 003 | RED [Red] | 3000.00 | 200 | Primary |
| Track | 004 | YLO [Yellow] | 1500.00 | 250 | Primary |

The attribute Type displays for the Color domain entity in the Product entity. Note that the values for Type correspond to the color of each product. Parent attribute names are labeled using the path to the parent domain entity, with the name of the domain attribute first, followed by the attribute.

The values for Color.Type are shown as shaded in the final example because they are always read-only. You cannot directly edit values for a parent attribute. You can, however, use the View Source Member option to open the parent entity. With the correct permissions, you can then edit values for the members of the domain entity. For more information, see [Viewing the Source Member](https://support.profisee.com/wikis/profiseeplatform/view_related_members).