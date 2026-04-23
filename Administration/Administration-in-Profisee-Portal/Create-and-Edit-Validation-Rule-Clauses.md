# Create and Edit Validation Rule Clauses

A data quality validation rule for an attribute validates an existing value. It is composed of one or more clauses, defined in a specific order. Additional clauses are created by clicking the **Plus**icon in the **Clauses** toolbar.

The clauses grid contains the following columns:

| Column | Description |
| --- | --- |
|  | The flag column displays error and warning indicators when there are configuration issues detected on the clause. |
| **Is Constraint** | This check box can be selected to make the rule a constraint. Constraint rules prevent users from creating or updating a record that violates that rule.  For example, if the rule "Name is required" is marked as a constraint, a user cannot create a new record with a blank Name attribute.  When rules with constraints are processed, any constraint failures are displayed when processed. |
| **Attribute Name** | This column is titled with the attribute name. This column contains a dropdown list of available rule operators. For details on each operator, refer to [Data Quality Rule Operators](https://support.profisee.com/wikis/profiseeplatform/data_quality_rule_operators). |
| **What** | Defines the parameter to which the specified attribute is compared. This field may be disabled if the assertion type selected does not support parameters. |
| **When** | Defines the optional condition that is applied to filter the members to which the assertion is made. |
| **Display Description** | Defines the user-friendly description for this rule when it  is displayed in Profisee FastApp Portal. |

To define a clause, perform the following steps:

1. [Add a new Data Quality Rule](https://support.profisee.com/wikis/profiseeplatform/creating_new_rules) or edit an existing one.
2. Click **Add** under the Validations tab to create a new clause.
3. Select an assertion from the dropdown list underneath the attribute name column.
4. If applicable, specify any required parameters in the **What** column using the [Expression Editor](https://support.profisee.com/wikis/profiseeplatform/using_the_expression_editor_in_portal). You can access this feature by clicking the **f(x)** icon that appears when an applicable assertion is listed.
5. Specify an optional **When** condition if desired. Click the **Ellipsis**icon to the right of the condition definition column. The **Rule Filter Condition** dialog opens.

Click the **Save** button to return to the main Clauses tab. The text expression for the created filter appears in the When column for the current clause.

6. Click **Save** or **Save and Close**.

---

## 