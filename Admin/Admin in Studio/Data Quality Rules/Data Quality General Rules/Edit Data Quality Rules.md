# Edit Data Quality Rules

Administrators can change the behavior of an existing rule by:

- Adding, deleting, and reordering rule clauses.
- Changing assertion types.
- Changing parameters and conditions.

To edit an existing rule:

1. Select a rule from the rules list.
2. Click **Edit**. The rule definition panel opens. Rule clauses are displayed as they were the last time the rule was saved.
3. Adjust the rule by:
1. Adding new clauses by clicking the **Add** icon in the rule definition panel. See [Create and Edit Validation Rule Clauses](https://support.profisee.com/wikis/profiseeplatform/create_and_edit_validation_rule_clauses) or [Create and Edit Assignment Rule Clauses](https://support.profisee.com/wikis/profiseeplatform/create_and_edit_assignment_rule_clauses) for more details.
2. Deleting an existing clause by clicking the **Delete** icon in the rule definition panel. The last clause cannot be deleted from the list but it can be changed.
3. Reorder clauses by clicking the icon in the rule definition panel.
4. Edit existing clauses by selecting the clause and changing its assertion, parameter, and/or condition properties.
5. Click **Save** or **Save and Close** to save the updated rule to the server. Click **Close** to close the rule definition panel without saving.

A rule becomes effective immediately on creation or update. Any master data changes in the entity are evaluated against the new or updated rule as soon as it is created. However, the rule is not evaluated on existing data unless an explicit request is made by the administrator to run rules for the entire entity. Refer to [Data Quality Rules Evaluation Process](https://support.profisee.com/wikis/profiseeplatform/data_quality_rules_evaluation_process) for details on running rules explicitly.

Administrators cannot delete or edit data quality rules while they are being processed.

Note that when a data quality rule is edited for an entity, validation issues that were triggered before the edit will still be displayed until the rules are processed on that entity.

## See Also

[Impact of Modeling and Rule Changes on the Data Quality Data Mart](https://support.profisee.com/wikis/profiseeplatform/impact_of_modeling_changes_on_the_data_quality_data_mart)