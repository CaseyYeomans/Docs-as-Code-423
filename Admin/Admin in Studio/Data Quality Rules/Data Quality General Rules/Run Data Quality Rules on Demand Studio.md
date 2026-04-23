# Run Data Quality Rules on Demand Using FastApps Studio

Use the **Run Rules** button when you want to select an entity, or multiple entities, and evaluate rules on the entire entity. **Run Rules** execution uses the data quality rule processing batch size established in System Settings. The Run Rules dialogue lists the processable entities alphabetically in two categories. Entities that require processing are listed first, and then entities that have not been edited since last processed (and do not require processing) are listed after.

## Related System Settings

**Data Quality Processing Batch Size** - The number of records evaluated and processed for rule assignments and violations. Processing batch size impacts the speed and efficiency of rules processing. The recommended value is between 100,000 and 200,000 records, depending on the size of the entity.

**Batch Size to Send** - The number of records sent in a batch to the server during publishing. This value also affects processing speed. The recommended value is 500.

## Procedure

To run data quality rules on demand:

1. Navigate to **Administration | Data Quality Rules**.
2. Click **Run Rules**. The Run Rules window opens.
3. Click the checkboxes to the left of the target entities.
4. Click **OK**.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i752bed6fbeebe663.png)

Review changes in your workspace entity view.

## Assignment Execution Mode

The Assignment Execution Mode determines which records have rules run on them. There are three settings:

- **Always**runs rules on all members regardless of type.
- **On Create Only** runs rules on newly created members.
- **On Update and on Demand** runs rules when a member is updated through interactive updates (this can be editing on the portal, on the entity grid, etc.) or staging, and when rules are run on demand for the whole entity.

## See Also

[Interactive Execution of Assignment Rules](https://support.profisee.com/wikis/profiseeplatform/interactive_execution_of_data_quality_rules)

[Command Line Utility Reference for Data Quality Rules](https://support.profisee.com/wikis/profiseeplatform/command_line_utility_reference_for_data_quality_rules)

[Data Quality Rules Overview](https://support.profisee.com/wikis/profiseeplatform/data_quality_rules_overview)