# Using the Relationship Manager

The Relationship Viewer is an interactive, modular interface that allows a user to visualize an established relationship. This interface presents the user with relationship cards that display the entities within a relationship, the attributes of those entities, and how those entities are related to each other. A user can navigate the Relationship Viewer to get a clear view of the full scope of a relationship, making it easy to visualize a relationship in a more tangible way than in a Relationship List.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ie745c1f590977a88.png)

## Opening and Closing the Relationship Viewer

A user in Profisee FastApp Portal with permissions to view a relationship can open the relationship viewer by right-clicking a record and selecting **View Relationships**. On Forms, click the **View Relationships** icon under the vertical ellipsis, or right click an entity within an entity grid context menu and select **View Relationships**.

This launches the Relationship Viewer in a pop-up window that covers the majority of the browser window. A user can press F11 to view the relationship in fullscreen mode.

To exit the Relationship Viewer, click the **X**icon on the top-right side of the window, or press the ESC key.

## Navigating the Relationship Viewer

The Relationship Viewer displays a relationship using one entity within the relationship as the subject, displaying all related entities with their appropriate predicates. If there are multiple entities in the same relationship, they will be shown as a stack of relationship cards.

For example: if a restaurant is viewed as the subject, there may be lines drawn to entities named "Customers" and "Supplier" with the predicates "serves" and "receives ingredients from" respectively. Because there are many customers, this relationship is displayed as a stack of cards with a number on the face indicating the number of records that are represented. However, if the restaurant only has one supplier, that entity will be displayed with its name and code.

To view the records within a stack of relationship cards, click the stack to launch a right-hand sidebar that displays the individual cards contained within the stack. Each card is displayed with the name and code of its entity.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i53be12f9f4d9bfea.png)

Note that the relationship viewer can only display eight kinds of relationships at a time. For relationship views with more than 8 relationship types, you can click the Forward and Backward pager at the bottom of the window to navigate to the next set of relationship types. 'Child' cards always appear as stacks even if they contain only one record.

If a relationship card is empty, you can select a record from a dropdown list to assign to the record.

You can navigate to a related record by hovering over a record in the sidebar and clicking it to expand. The card expands and becomes the new subject of the relationship, allowing you to further navigate to records related to the selected record. The previously selected record becomes a tab in the top-left of the screen that can be clicked to return to the previous record.

![Image](https://profisee.visualstudio.com/ad098ab8-fc30-4fe4-982d-460e6c9eb694/_apis/wit/attachments/4a85e14d-8611-4558-b62f-d6cc47ded0c5?fileName=image.png)

You can add a new relevant record to the stack by clicking the **+**icon on the same sidebar. You can also edit or clear DBA values by clicking the respective icons on a card header.

### Many to Many Relationships

When using a Many to Many relationship, additional options are available in the Child Slideout control. By clicking the relationship card stack, the associated records appear in the Child Slideout. Here, entities with the same Code value indicate bridge records for this relationship. To see the difference between the bridge records, you can hover over the card header and click the **Relationship** icon to see the bridge table values for this vendor on the first card, and again on the second card to open the default form for the bridge entity.

![](https://profisee.visualstudio.com/ad098ab8-fc30-4fe4-982d-460e6c9eb694/_apis/wit/attachments?FileNameGUID=594c3ea7-d708-455a-b1e7-5a62ea15a459&FileName=tmp26BE.png)To see more information about the child, click the 'eye' icon to open the default form for the entity. If desired, you can click the Delete button to remove the bridge entity record.

![](https://profisee.visualstudio.com/ad098ab8-fc30-4fe4-982d-460e6c9eb694/_apis/wit/attachments?FileNameGUID=996a0af2-905a-4142-aae8-ad8af39d5d2a&FileName=tmp4C01.png)

The Relationship Manager cannot display Many-to-Many relationships where Entity 1 and Entity 2 are the same entity, even when these relationships are valid. To engage with these kinds of relationships in the Relationship Manager, it is recommended to create two duplicate entities for Entity 1 and Entity 2 with different parent-child relationships to the bridge entity **OR** to use a Relationship List on a form.