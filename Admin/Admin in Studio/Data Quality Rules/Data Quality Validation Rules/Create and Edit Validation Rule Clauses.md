# Create and Edit Validation Rule Clauses

A data quality validation rule for an attribute validates an existing value. It is composed of one or more clauses, defined in a specific order. Additional clauses are created by clicking the **Plus**icon in the **Clauses** toolbar.

The clauses grid contains the following columns:

| Column | Description |
| --- | --- |
| | The flag column displays error and warning indicators when there are configuration issues detected on the clause. |
| **Is Constraint** | This check box can be selected to make the rule a constraint. Constraint rules prevent users from creating or updating a record that violates that rule. For example, if the rule "Name is required" is marked as a constraint, a user cannot create a new record with a blank Name attribute. When rules with constraints are processed, any constraint failures are displayed when processed. |
| **Attribute Name** | This column is titled with the attribute name. This column contains a dropdown list of available rule operators. For details on each operator, refer to [Data Quality Rule Operators](https://support.profisee.com/wikis/profiseeplatform/data_quality_rule_operators). |
| **What** | Defines the parameter to which the specified attribute is compared. This field may be disabled if the assertion type selected does not support parameters. |
| **When** | Defines the optional condition that is applied to filter the members to which the assertion is made. |
| **Display Description** | Defines the user-friendly description for this rule when it is displayed in Profisee FastApp Portal. |

To define a clause, perform the following steps:

1. [Add a new Data Quality Rule](https://support.profisee.com/wikis/profiseeplatform/add_data_quality_rules) or [Edit an existing one](https://support.profisee.com/wikis/profiseeplatform/edit_data_quality_rules).
2. Click **Add** under the Validations tab to create a new clause.
3. Select an assertion from the dropdown list underneath the attribute name column.
4. If applicable, specify any required parameters in the **What** column using the [Expression Editor](https://support.profisee.com/wikis/profiseeplatform/use_the_expression_editor). You can access this feature by clicking the **f(x)** icon that appears when an applicable assertion is listed.
5. Specify an optional **When** condition if desired. Click the **Ellipsis**icon to the right of the condition definition column. The **Rule Filter Condition** dialog opens.

Construct the rule filtering by adding one or more filter conditions. For more details on constructing filters, refer to the following topics:

1. [Build an entity grid filter](https://support.profisee.com/wikis/profiseeplatform/build_an_entity_grid_filter)
2. [Multi-line entity grid filters](https://support.profisee.com/wikis/profiseeplatform/multi_line_entity_grid_filters)
3. [Filter Using Parent Attributes](https://support.profisee.com/wikis/profiseeplatform/filter_using_parent_attributes)

Click the **Save** button to return to the main Clauses tab. The text expression for the created filter appears in the When column for the current clause.

6. Click **Save** or **Save and Close**.

## See Also

[Impact of Modeling and Rule Changes on the Data Quality Data Mart](https://support.profisee.com/wikis/profiseeplatform/impact_of_modeling_changes_on_the_data_quality_data_mart)