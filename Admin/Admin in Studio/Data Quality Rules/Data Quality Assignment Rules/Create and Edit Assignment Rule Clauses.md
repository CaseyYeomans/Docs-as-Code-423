# Create and Edit Assignment Rule Clauses

An assignment rule clause sets the value of an attribute when an optionally specified condition is true. An assignment rule for an attribute is composed of one or more clauses, defined in a specific order. Clauses are created by clicking the **Plus** icon in the Clauses toolbar. Like validation clauses, the clauses are evaluated in the order that they appear in the clauses grid. The assignment clause applied is the first clause that passes the specified **When** condition. The net effect of this is that an assignment rule should have at most one clause with no condition and that clause must be the last clause in the list.

The clauses grid contains the following columns:

| Column | Description |
| --- | --- |
| | The flag column displays error and warning indicators when there are configuration issues detected on the clause. |
| **Name** | The assignment type column is titled with the attribute name and is intended to be read as (for example) "Name equals". This column contains a drop-down list of available assignment types. |
| **What** | Defines the static or relative value or an attribute from which the target attribute receives its value. This field may be disabled if the assertion type selected does not support parameters. |
| **When** | Defines the optional condition that is applied to filter the members to which the assignment is made. |

To define a clause, perform the following steps:

1. Select the assignment type from the **Attribute Name** column.
2. Specify any required parameters in the **What** column. A parameter can be either a type-consistent constant value or a reference to another attribute on the same entity or a different entity. Attribute parameters are selected using the **Multilevel Attribute Selector** dialog. Click the **Ellipsis**icon to the right of the **What** input field.
3. Specify an optional When condition if desired. Click the **Ellipsis**icon to the right of the condition definition column. The **Rule Filter Condition** dialog opens.
4. Construct the rule filtering by adding one or more filter conditions. For more details on constructing filters, refer to the following topics:
1. [Build an Entity Grid Filter](https://support.profisee.com/wikis/profiseeplatform/build_an_entity_grid_filter)
2. [Multi-line Entity Grid Filters](https://support.profisee.com/wikis/profiseeplatform/multi_line_entity_grid_filters)
3. [Understand Status Attributes](https://support.profisee.com/wikis/profiseeplatform/understand_status_attributes)
4. [Filter using Parent Attributes](https://support.profisee.com/wikis/profiseeplatform/filter_using_parent_attributes)
5. Click **Save** to return to the Assignment clauses tab. The text expression for the created filter appears in the When column for the current clause.

## Relative Date/Time Assignment

When working with a date-related attribute, the Assignment clause tab displays options for date and time . Select a value from the drop-down, or select a custom date.

### Select a Relative Date

Choose a relative date type **Custom**from the dropdown menu. If you choose Custom, you'll be prompted for the specific date to use for the assignment. Available dropdown values are:

| | |
| --- | --- |
| Custom | End of Month |
| Today | Next Month |
| Yesterday | Start of Quarter |
| Tomorrow | End of Quarter |
| Start of Week | Next Quarter |
| End of Week | Start of Year |
| Next Week | End of Year |
| Start of Month | Next Year |

### Select a Custom Date

1. Click **Custom**. A calendar pop-up opens.
2. Use the navigation arrows to select the desired date.

## Assignment Execution Mode

The Assignment Execution Mode determines which records have rules run on them. There are three settings:

- **Always** runs rules on all members regardless of type.
- **On Create Only** runs rules on newly created members.
- **On Update and on Demand** runs rules when a member is updated through interactive updates (this can be editing on the portal, on the entity grid, etc.) or staging, and when rules are run on demand for the whole entity.

## See Also

[Impact of Modeling and Rule Changes on the Data Quality Data Mart](https://support.profisee.com/wikis/profiseeplatform/impact_of_modeling_changes_on_the_data_quality_data_mart)