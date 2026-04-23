# Delete Data Quality Rules

Administrators can delete rules from the main rules grid in the Data Quality Rules administration tab. Deleted rules are removed from the associated attribute.

To delete a rule:

1. Select the rule or rules from the rules list. Multiple rules can be selected by using *<Shift>Right-Click* or *<Ctrl>Right-Click* to select contiguous or specific rules from the grid.
2. Click the Delete icon on the rules administration toolbar. A confirmation dialog opens.
3. Click **Yes** on the confirmation dialog or click **No** to cancel the delete request.

Administrators cannot delete or edit data quality rules while they are being processed.

Administrators should explicitly run rules on the affected entity to ensure any existing issues related to deleted rules are closed as obsolete.

Note that when a data quality rule is deleted, validation issues that were triggered before the deletion will still be displayed until the rules are processed.

If all rules are deleted on an entity, an automatic process removes all existing validation rule flags. To avoid inaccurate errors from being displayed, wait for this process to complete before creating new data quality rules for that entity.

## See Also

[Impact of Modeling and Rule Changes on the Data Quality Data Mart](https://support.profisee.com/wikis/profiseeplatform/impact_of_modeling_changes_on_the_data_quality_data_mart)