# Add Data Quality Rules

Administrators can add new rules to the rule inventory by clicking the icon in the toolbar. You can create one rule per attribute. The rule can have one or more clauses asserting different conditions the attribute must meet to be considered valid.

To add a new rule, perform the following steps:

1. Click the **Plus**icon in the toolbar. The **Create New Rule** window opens.
2. Select the desired entity.
3. Select the desired attribute. The **Attribute** dropdown list excludes attributes that already have rules.
4. Click **OK**. The rule definition panel opens. Click **Cancel** to abort the rule creation process.
5. Specify one or more clauses for the rule. See [Create and Edit Validation Rule Clauses](https://support.profisee.com/wikis/profiseeplatform/create_and_edit_validation_rule_clauses) or [Create and Edit Assignment Rule Clauses](https://support.profisee.com/wikis/profiseeplatform/create_and_edit_assignment_rule_clauses) for detailed steps.
6. Use the the arrow buttons to change the order of the clauses.
7. Click **Save** or **Save and Close** to save the rule to the server. Click **Close** to close the rule definition panel without saving.

A rule becomes effective immediately on creation or update. Any master data changes in the entity are evaluated against the new or updated rule as soon as it is created. However, the rule is not evaluated on existing data unless an explicit request is made by the administrator to run rules for the entire entity. Refer to [Data Quality Rule Evaluation Process](https://support.profisee.com/wikis/profiseeplatform/data_quality_rules_evaluation_process)for details on running rules explicitly.

## See Also

[Impact of Modeling and Rule Changes on the Data Quality Data Mart](https://support.profisee.com/wikis/profiseeplatform/impact_of_modeling_changes_on_the_data_quality_data_mart)