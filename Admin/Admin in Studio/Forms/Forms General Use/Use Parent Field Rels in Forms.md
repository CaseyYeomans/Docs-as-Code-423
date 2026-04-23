# Use Parent Field Relationships in Forms

For information on creating field relationships in forms, see [Manage Field Relationships](https://support.profisee.com/wikis/profiseeplatform/manage_field_relationships). For information on creating a FastApps Portal application, see [Create a New FastApps Portal Application](https://support.profisee.com/wikis/profiseeplatform/create_a_new_fastapp).

By adding parent fields using DBAs in multiple entities, it is possible to add DBA lists in forms that are chained together and driven by previous selections. Child DBA lists are constrained by the selected parent, which presents a narrower group of options to the end user. Selection begins with the most general DBA attribute and works toward the most specific, constraining each subsequent DBA list based on the previous selection. When a DBA contains numerous values, making selections in this way can limit the number of options presented to users to only those that are needed. This can speed up data entry on forms by simplifying the way users enter data.

Consider an example of a user that must complete new employee information, which includes selecting a home office for the new employee. The user will enter new member information using an Add Member form in an entity grid control embedded in a FastApps Portal application page.

This is the Employee entity:

| | | | | |
| --- | --- | --- | --- | --- |
| Employee Name | Employee ID | Title | Exempt | Home Office City |
| Emma Gold | 001 | Line Supervisor | N | Greensboro |
| Fred Blue | 002 | Senior Data Developer | Y | San Diego |
| Elizabeth Green | 003 | Customer Service Representative | N | Toronto |
| Jeremy Crimson | 004 | Order Picker | Y | Winnipeg |

When a user adds a new employee, a value for the Home Office City DBA must be included. There are 500 possible values for the Home Office City attribute. Scrolling through this list takes the user additional time to locate the necessary value, but parent fields can make finding the correct value in a long list like this a simpler process.

This is the City entity. It is the domain for the Home Office City attribute in the Employee entity, and it also includes a DBA called StateProvince.

| | | |
| --- | --- | --- |
| Name | Code | StateProvince |
| Greensboro | 500A | NC |
| San Diego | 250s | CA |
| Toronto | 75-91A | ON |
| Winnipeg | RL-890 | MB |
| Calgary | CA5679 | AB |
| Hickory | 536B | NC |
| Redding | B1358 | CA |
| Lincoln | RQ-7834 | NE |

This is the StateProvince entity, which is the domain for the StateProvince DBA in the previous entity example. It includes a DBA called Country.

| | | |
| --- | --- | --- |
| StateProvince | Code | Country |
| NC | 9999 | United States |
| CA | 9998 | United States |
| ON | 9997 | Canada |
| MB | 9996 | Canada |
| AB | 9995 | Canada |
| NE | 9994 | United States |

This is the Country entity, which is the domain for the Country attribute in the previous entity.

| | |
| --- | --- |
| Country | Code |
| United States | US |
| Canada | CA |

The Add Member form for this entity (used with an entity grid control in FastApps Portal) looks like this:

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i4a33e0fb93f95820.png)

The entity used to create the form is the Employee entity. The Name and Code fields are the attributes for the Name and Code attributes in the entity. Adding the Home Office City DBA makes it possible to add the StateProvince attribute as a parent field. From the StateProvince field, it is then possible to add the Country attribute as a parent field. Parent fields are linked through DBAs in entities.

One child attribute can have more than one parent. To add a second parent, add the DBA you want to act as the second parent to the Form layout. RIght-click the child field and select **Manage field relationships**. On the **Parent**tab, select the previously added DBA, then click **Close.**![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i89cb64a1c64d9fe2.png)

When complete, the form is added to an entity grid control in a FastApps Portal application page as the Add Member form. Users with the correct permissions can then access the entity and add new members to the Employee entity using the form.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-ia4078f0ed2f68d67.png)

The user can type in a Name and Code for a new employee. Then, instead of having to look through hundreds of Home Office City values, the user can make two selections to narrow down the possible options for Home Office City. The user begins with the Country list and selects either Canada or United States. This constrains the StateProvince list to valid selections for the US or for Canada. When the user makes a selection from the StateProvince list, the list displayed in the Home Office City is limited to cities in that state or province. From this much smaller list, the user can select the correct city.

Notice that StateProvince and Home Office City are not enabled in the form; only the Country list is enabled. Parent fields require that users make the selection within the entity last (in this case, Home Office City) and begin with the most general selection (Country) first. Each subsequent field is enabled when the user makes a selection from the previous list.