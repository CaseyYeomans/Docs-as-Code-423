# Structure Unstructured Data with the AI Assistant

Profisee Administrators can use Connect to take unstructured data within their instance and meaningfully pair it to appropriate entities. This can be used to automatically organize large, unpaired data sources that would be time-consuming to manually extract and structure.

To structure unstructured data with the AI Assistant:

1. Navigate to the **Strategies** tab of **Connect** inside the Administration section of Profisee portal.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id0202d9245e00390.png)
2. Click the **+** icon to add a new integration strategy.
3. Create a new strategy using the **AI Structure Data** Service Configuration, including a strategy name and selecting the entity containing the data you wish to structure.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i79102352e6155fda.png)
4. Click **Continue**. The **Configuration Details** view opens.

From here, you must complete configuration on the Overview, Structure Data, Run Options, and Scheduling tabs.

### Overview

The Overview tab displays read-only (except for the editable Strategy Name) details about the strategy, including:

* **Strategy Name**: The name of the Strategy
* **Configuration**: The Service Configuration used in the strategy
* **Source Entity**: The entity containing the unstructured data
* **Entity**: The entity the strategy is applied to

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3f9cafcc5c1b0d3.png)

### Structure Data

The Structure Data tab contains mapping tools allowing you to manually map attributes, or allow the AI Data Assistant to [manually map attributes](https://support.profisee.com/wikis/profiseeplatform/Data_Mapping_with_Open_AI) for you.  ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i19c48eff72804a83.png)

1. Select a target entity in the *Type to Search* bar for the **Unstructured Data Location**. This must be a Text Attribute containing the unstructured data.
2. Assign Customer Attributes from the Configuration details pane by clicking the **+** icon to manually add attributes that match OR click the [Aisey AI](https://support.profisee.com/wikis/profiseeplatform/using_the_profisee_AI_assistant_in_portal) **Suggest** button to preview AI-generated suggestions for the attribute mappings, then click **Submit** when you are satisfied with the suggestions to automatically apply them in bulk. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i8524a7f3b4329f85.png)
3. Click the **Assign** checkbox to confirm the Customer Attributes you wish to match with the suggested attributes.
4. Click **Save** or **Save and Close** to apply the changes.

## Run Options

When selecting the Run Options for a Strategy with an Export integration flow, continuous execution options are available, such as when records are added, updated, or deleted.

When choosing to execute continuously on record delete, you can choose whether to flag the record in the external system for deletion or to delete the record in the external system.

An optional record filter can be applied to each continuous option to limit the number of records to be processed for each of the continuous options.

### Schedules

Users can add one or more named schedules. A unique name for each schedule is provided by default, but this value can be updated if needed. A new schedule must be added as a [Cron expression](https://cronevery.day/).

---