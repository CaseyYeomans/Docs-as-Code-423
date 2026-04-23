# Interactive Execution of Data Quality Rules

Interactive execution of data quality rules acts on changes **per transaction** when those changes are published. The following actions will initiate the execution of rules in the FastApps Studio client:

- Member creates and updates to the entity grid in FastApps Studio
- Data deployment
- Member creates and updates in FastApps Portal

## On Transaction

When member information changes are published, any applicable assignment and validation rules will be run. Refresh the display to see changes after rules are run.

The following is an example of this process:

1. In the Product entity, we change the Style value in the six selected members from **U [Uni]** to **M [Men's]**.

The applicable data quality rules are shown below.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i5e74ab3a805a0ac8.png)
2. Click **Publish**. A confirmation window opens.
3. Click **Yes**.
4. The bike color has changed to **BLK** based on the applied assignment rules.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i167a2440dd011947.png)

## Assignment Execution Mode

The Assignment Execution Mode determines which records have rules run on them. There are three settings:

- **Always**runs rules on all members regardless of type.
- **On Create Only** runs rules on newly created members.
- **On Update and on Demand** runs rules when a member is updated through interactive updates (this can be editing on the portal, on the entity grid, etc.) or staging, and when rules are run on demand for the whole entity.

Note that **no real time data quality rules evaluation will occur** if Logging on Entity is set to **None**.

## See Also

[Data Quality Rules Overview](https://support.profisee.com/wikis/profiseeplatform/data_quality_rules_overview)

[Run Data Quality Rules on Demand using FastApps Studio](https://support.profisee.com/wikis/profiseeplatform/run_data_quality_rules_on_demand)