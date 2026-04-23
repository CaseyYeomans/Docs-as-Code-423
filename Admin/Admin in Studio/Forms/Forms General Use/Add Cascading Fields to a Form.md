# Add Cascading Fields to a Form

Cascading fields let you display and edit information about a member in a hierarchical manner when entities are designed to support it. This concept is explained as follows by means of an example. The DBAs which link the different entities together are color-coded, showing the DBAs as values and also as domain entity members.

The following example uses bike models with different paint options to illustrate the way cascading fields function in a form.

For example, this is a Product entity. Color is a DBA in the entity.

| | | | | |
| --- | --- | --- | --- | --- |
| Name | Code | Color | StandardCost | ReorderPoint |
| Mountain | 001 | BLK [Black] | 1200.00 | 800 |
| Touring | 002 | BLK [Black] | 1400.00 | 500 |
| Racing | 003 | RED [Red] | 3000.00 | 200 |
| Track | 004 | YLO [Yellow] | 1500.00 | 250 |

This is the domain of the Color DBA. Type is a DBA in the entity.

| | | |
| --- | --- | --- |
| Name | Code | Type |
| Black | BLK | Neutral |
| Beige | BEI | Neutral |
| Red | RED | Primary |
| Yellow | YLO | Primary |
| Silver | SVR | Metallic |

This is the domain of the Type DBA. Availability is a DBA in the entity.

| | | |
| --- | --- | --- |
| Name | Code | Availability |
| Neutral | NEU | Stock |
| Primary | PRI | Custom |
| Metallic | MET | Custom |
| Matte |