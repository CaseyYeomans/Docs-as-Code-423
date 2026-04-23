# Multi-line Entity Grid Filters

The entity grid filter makes it possible to create filters containing multiple statements to build complex filters. For information on basic entity grid filter options, see [Building an entity grid filter](https://support.profisee.com/wikis/profiseeplatform/build_an_entity_grid_filter).

## Adding Multiple Lines

- To insert an additional filter condition in the Filter and Sort dialog, click **Insert** to add a new line.

Multi-line filters let you filter an entity using multiple attributes at once. By default, all statements are joined by AND. In addition to the default AND operator, you can also join filter statements using OR.

**Example**:

| | |
| --- | --- |
| | **Name contains mountain** |
| **AND** | Color equals Black |
| **AND** | StandardCost > 500 |

The grid displays only the members that have all of these three qualities.

Alternatively, using OR logic:

**Example**:

| | |
| --- | --- |
| | **Name contains mountain** |
| **OR** | Color equals Black |
| **OR** | StandardCost > 500 |

The grid displays the members that have any of these three qualities.

## Grouping

You can group multiple conditions together to create complex filters.

To group two or more filter conditions:

1. In the Filter and Sort dialog, create two or more filter conditions.
2. Select two or more adjacent conditions, and then click **Group**.

A mark appears in the Group column next to each grouped statement.
3. Using the options in the **And/Or** column, select the appropriate operator for the grouped filter condition.

**AND**: The filter statement before as well as the grouped statement must be true to match the filter

**OR**: Either the filter statement before or the grouped statement must be true to match the filter.
4. Using the options in the **And/Or** column, select the appropriate operators for the filter conditions within the grouped statement.
5. Click **Save**.

**Example**:

| | | |
| --- | --- | --- |
| | | **Name contains mountain** |
| **AND** | [ | Color equals Black |
| **OR** | Color equals Yellow |

The grid displays all members with Mountain in the name with a color of black or yellow.

Notes

- Grouped filter statements can contain many more than two conditions, and can be nested inside other grouped conditions.
- The And/Or operator applies to the condition (or group) on the same line and to the line (or group) appearing just before it. This is why the first condition in the list does not have a grouping option.

## Ungrouping

To ungroup two or more filter conditions:

1. In the Filter and Sort dialog, select the grouped conditions.
2. Click **Ungroup**.

The filter conditions now appear as independent conditions.

## Reordering

The reordering options let you arrange filter conditions the way you prefer. Reorder conditions to move them to adjacent positions for grouping. Otherwise, filter condition order is unimportant.

To reorder filter conditions:

1. In the Filter and Sort dialog, select a filter condition.
2. Click **Move selected up** to move the condition up a row, or click **Move selected down** to move it down a row.

The filter condition now appears in the new position.