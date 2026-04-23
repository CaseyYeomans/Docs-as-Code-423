# Filter Using Parent Attributes

In addition to filtering an entity using values of attributes in that entity, you can also filter entities using attributes in parent entities. This is possible when a domain-based attribute in the entity uses another entity as its domain. Through this reference, you can use any attributes in the domain entity as filter criteria.

For example, consider the following two data members Mountain and Touring in a Product entity (where Color is a domain-based attribute):

**Product entity**

| | | | |
| --- | --- | --- | --- |
| Name | Code | Color | Days to Manufacture |
| Mountain | 001 | Black {BLK} | 1 |
| Touring | 002 | Red {RED} | 5 |

And the following data members in the Color entity (the domain entity for the Color DBA in the Product entity):

**Color entity**

| | | |
| --- | --- | --- |
| Name | Code | MinimumDays |
| Black | BLK | 2 |
| Red | RED | 3 |

You can filter the Product entity using the following entity grid filter:

Color.MinimumDays > Days to Manufacture

For the member Mountain, Days to Manufacture = 1, and because the Color member BLK has a value of 2 for MinimumDays, the filter is interpreted as:

**2 > 1**

This is true, so member Mountain displays when the filter is applied to the Product entity.

For the member Touring, Days to Manufacture = 5, and because the Color member RED has a value of 3 for MinimumDays, the filter is interpreted as:

**3 > 5**

This is not true, so member Touring does not display when the filter is applied to the Product entity.

In the example above, you can filter using Color.MinimumDays within the Product entity, even though MinimumDays is not directly applied to products. Profisee can find the path to the MinimumDays attribute by following the DBA reference back to the Color entity.

## See Also

[Understanding Parent Attributes](https://support.profisee.com/wikis/profiseeplatform/understand_parent_attributes)