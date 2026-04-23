# Configuring a Data Quality Agent

The Aisey Data Quality Agent automatically fixes missing or invalid attribute values by using AI to infer the correct data based on contextual information from other fields. The agent runs as a specified run-as user, and will autonomously perform data quality tasks as it detects data quality issues. After clicking **Continue** from the creation dialog, you can configure the agent using four tabs.

Note that the Data Quality Agent only runs on records with validation issues.

### Overview Tab

The Overview tab displays the basic agent configuration. You can review and edit the following information:

* **Agent Name**: The name given for the agent (editable)
* **Agent Type**: Displays "Data Quality Agent" (read-only)
* **Model**: The AI model used by this agent (editable dropdown)
* **Entity**: The entity this agent operates on (read-only)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5b9100df96d25f5c.png)

### Auto-Fix Data Tab

The Auto-Fix Data tab is where you configure the logic for how the agent identifies and fixes data quality issues. This tab allows you to specify which attribute should be fixed, provide context for the AI model, and select input attributes that will help the model make accurate predictions.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id1da5a979285daad.png)

#### Attribute to Fix

Select the attribute that should be monitored and automatically treated by the AI agent. This is typically an attribute with a requirement rule that results in records becoming invalid when the field is empty or contains incorrect data. The field includes a "Type to Search" field to locate specific attributes within your entity.

#### Agent Prompt

Enter clear guidance for the AI model that explains how it should approach fixing the invalid attribute. The prompt should provide specific instructions that help the model understand the context and business logic.

Examples of effective prompts:

* "Use the company name and address to find the company's website"
* "Based on the company name and industry, determine the appropriate industry code"
* "Using the customer's name and location, infer the missing phone number"

#### DBA Record Limit'

Select the maximum number of records in a DBA that blank

#### Input Attributes (Context)

Select one or more entity attributes that should be provided to the AI model as context. These attributes help the model make informed decisions about what value to fill in for the invalid attribute.

The input attributes selector displays attributes in a specific order:

* **Name** and **Code** appear first (if available)
* All other attributes are listed alphabetically

Choose attributes that are most likely to contain relevant information for inferring the missing value. For example, if fixing a Website attribute, you might select Company Name, Address, and Industry as input attributes.

Input attributes cannot be edited or reordered. They are displayed in a fixed order with Name and Code at the top, followed by other attributes alphabetically.

### Run Options Tab

The Run Options tab determines how and when the agent executes. You can choose to run the agent when a record is added, when a record is updated, or both.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i7b24c7609d690377.png)

* **Run-as user**:The account used to make changes when the Agent is triggered.
* **Triggers when records are added:**Causes the agent to run any time records are added to the entity.
* **Added records filter:**Allows you to create an expression that limits the above option to run only when the records added meet certain criteria.
* **Trigger when records are updated:**Causes the agent to run any time records in the entity are updated.
* **Updated records filter:**Allows you to create an expression that limits the above option to run only when the records edited meet certain criteria.

### Scheduling Tab

The Scheduling tab allows you to define optional schedule expressions that control when the agent executes. This provides an alternative to continuous execution if you prefer to run the agent at specific times or intervals.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic6c6f72fd260a0b7.png)

If you want to execute the agent on a schedule, create a schedule by adding a name and Cron expression to the options under the Scheduling tab. If left blank, the agent will run based on the execution mode selected in the **Run Options** tab (either on-demand or continuous).

Example scheduling expressions:

* **0 0 \* \* \***: Run daily at midnight
* **0 \*/6 \* \* \***: Run every 6 hours
* **0 0 \* \* 1**: Run weekly on Mondays at midnight

You can also create [expressions](https://support.profisee.com/wikis/profiseeplatform/using_the_expression_editor_in_portal) that trigger based on data conditions, such as when validation status changes to a specific value.

## Saving Your Agent

After configuring your agent across all tabs, use the buttons at the bottom of the form to save your work:

* **Save**: Saves your changes and keeps the agent configuration form open for further editing
* **Save and Close**: Saves your changes and returns you to the Agents grid
* **Cancel**: Closes the form without saving any changes made since the last save

---