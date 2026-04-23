# Create Sibling Relationships Between Form Attributes

When you create a form, the entity in the context of the form may not include the attribute relationships that you want to use. The **Manage field relationships** dialog in Forms lets you use the relationships between attributes in a different entity for the entity in your form.

You must have the following to create sibling relationships:

- An entity containing all of the attributes you want to include in the relationship
- A bridge table containing the attributes with the correct relationships already established
- A form containing two or more field controls for domain-based attributes that exist in both the entity and bridge table

Consider the following Product entity containing a list of bike models:

| Name | Code | Color | Style | Finish | Effect |
| --- | --- | --- | --- | --- | --- |
| Mountain ABC | 001 | Red | M | Matte | Metallic |
| Mountain DEF | 002 | Black | M | Matte | Glitter |
| Touring ABC | 003 | Blue | M | Gloss | None |
| Touring DEF | 004 | Black | U | Gloss | Metallic |
| Mountain GHI | 005 | Purple | U | Hi Gloss | Glitter |
| Mountain JKL | 006 | Green | W | Hi Gloss | None |
| Mountain MNO | 007 | Red | W | Matte | Metallic |
| Touring GHI | 008 | Black | W | Gloss | Glitter |
| Touring JKL | 009 | Blue | W | Hi Gloss | None |

Color, Finish and Effect are domain-based attributes (DBAs). There could be other attributes in this entity, such as price, class, size, and other characteristics of a particular bike model.

These are the domains for the DBAs in the entity:

Color entity (the domain for the Color DBA)

| | |
| --- | --- |
| Name | Code |
| Red | RED |
| Black | BLA |
| Blue | BLU |
| Purple | PUR |
| Green | GRE |
| Yellow | YEL |

Finish entity (the domain for the Finish DBA)

| | |
| --- | --- |
| Name | Code |
| Matte | MAT |
| Hi Gloss | HIG |
| Gloss | GLO |

Effect entity (the domain for the Effect DBA)

| | |
| --- | --- |
| Name | Code |
| Glitter | GLI |
| Metallic | MET |
| None | NON |

If you included the Product entity in a form, an end user could choose any combination of Color, Style, Finish and Effect. There are no relationships between these attributes, so any selection is valid. However, the producer of these bike models does not offer unlimited combinations of the paint styles. There are only a few that are valid. You could choose to validate the selections with business rules, but it is more efficient to construct forms where users can only make valid selections.

This is accomplished by first creating a bridge entity (table) that defines the valid relationships between the DBAs.

This bridge table is called the Paints entity, and it includes the valid paint color, finish and effect combinations, along with the color names provided by Marketing.

The Paints entity:

| | | | | |
| --- | --- | --- | --- | --- |
| Name | Code | Color | Finish | Effect |
| Nail Polish | NAI | Red | Matte | None |
| Candy Apple | CAP | Red | Hi Gloss | Glitter |
| Cosmos Blue | COB | Blue | Gloss | Metallic |
| Galaxy | GAL | Black | Gloss | Glitter |
| Ink | INK | Black | Matte | None |
| Meadow | MEA | Green | Hi Gloss | None |
| Purple Haze | PUR | Purple | Matte | Glitter |
| Hazard | HAZ | Yellow | Matte | Glitter |

If you create a form with the Product entity, and add the Name, Color, Finish, and Effect attributes to it, you will be able to create a bike with paint combinations that don't exist in the Paint bridge entity. However, bikes are only available with the combinations defined by the bridge table.

If you create a form with these field controls without any relationships, you can make any selections for the DBAs:

**Color** = list contains all color members in the Color domain

**Finish** = list contains all finish members in the Finish domain

**Effect** = list contains all effect members in the Effect domain

If you make Color, Finish, and Effect siblings of each other (for more information, see [Manage Field Relationships](https://support.profisee.com/wikis/profiseeplatform/manage_field_relationships)), then the constraints in the bridge table between the attributes will also exist in the form.

The same fields with sibling relationships between the three attributes when **Color = Red**:

**Color** = **Red**

**Finish** = **Matte**, **Hi Gloss**

**Effect** = **None**, **Glitter**

This outcome occurs because there are only two possible paint colors where the Color is Red:

| | | | | |
| --- | --- | --- | --- | --- |
| Nail Polish | NAI | Red | Matte | None |
| Candy Apple | CAP | Red | Hi Gloss | Glitter |

Because the fields are siblings in a many-to-many relationship, the selection of any value for any attribute drives the selections available for the others. When Color = Red and Finish = Matte, the selections are as follows:

**Color** = **Red**

**Finish** = **Matte**

**Effect** = **None**

There is only one possible combination where the Color is Red and the Finish is Matte:

| | | | | |
| --- | --- | --- | --- | --- |
| Nail Polish | NAI | Red | Matte | None |

Similarly, when **Effect** = **None**, then your possible selections are as follows:

**Color** = **Red**, **Black**, **Green**

**Finish** = **Matte** or **Hi Gloss**

**Effect** = **None**

The list selections reflect the three valid paint combinations:

| | | | | |
| --- | --- | --- | --- | --- |
| Nail Polish | NAI | Red | Matte | None |
| Ink | INK | Black | Matte | None |
| Meadow | MEA | Green | Hi Gloss | None |

Ensure all desired combinations of members and attributes within the bridge table are captured within the first 500 records. Entries that are entered later may not be properly displayed in the relationship viewer on the portal.

To view the first 500 records, sort the bridge table by Code in ascending order.