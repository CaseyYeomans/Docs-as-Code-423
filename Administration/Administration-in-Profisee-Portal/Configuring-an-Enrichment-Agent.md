# Configuring an Enrichment Agent

The Aisey Enrichment Agent automatically generates or populates attribute values by using AI to create contextual, meaningful content based on information from other fields. Unlike the Data Quality Agent which fixes invalid data, the Enrichment Agent enhances valid but incomplete data by intelligently generating new values such as product descriptions, marketing copy, or summarized account details. The agent runs as a specified run-as user and will autonomously perform enrichment tasks based on the triggers and schedules you configure.

### Overview Tab

The Overview tab displays the basic agent configuration in a **Configuration Details** section. You can review and edit the following information:

* **Agent Name**: The name given for the agent (editable, required)
* **Agent Type**: Displays "Enrichment Agent" (read-only)
* **Model**: The previously configured AI model used by this agent (editable dropdown, required)
* **Entity**: The entity this agent operates on (read-only)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-idd525ea84343ac08.png)

### Enrich Data Tab

The Enrich Data tab allows you to configure the logic for how the agent identifies which attributes to populate and what information to use when generating new values. This tab is divided into two main sections: **Source** and **Input Attributes (Context)**.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iadc2c13d5fbd6769.png)

#### Source Section

The Source section defines what attribute will be enriched and how the AI should approach the enrichment.

**Attribute to Enrich**

Select the attribute that should be automatically populated by the AI agent. This is typically a descriptive or summary field that benefits from AI-generated content, such as marketing descriptions, product summaries, or categorization fields. The field includes a "Type to search" dropdown to help you quickly locate specific attributes within your entity. This is a required field.

**Domain-Based Attributes**

 If the target attribute to enrich is a domain-based attribute (DBA), the available values will be passed to the AI model to select from, up to the limit specified in the DBA Record Limit field.

**Agent Prompt**

Enter clear, specific instructions for the AI model that explain how it should approach enriching the attribute. The prompt should provide guidance that helps the model understand the context, tone, and business requirements for the generated content. Use the text area to enter your custom prompt.

Examples of effective prompts:

* "Generate a short, compelling marketing description using the product's name, features, and category"
* "Use the company name and address to find the company's website"
* "Based on the product's features and category, write a 2-3 sentence product summary"
* "Using the account's industry and size, generate appropriate account classification"

The quality and relevance of the AI-generated content depends significantly on how well you craft this prompt. Be specific about the desired output format, length, and tone.

**DBA Record Limit**

When the attribute to enrich is a domain-based attribute, this setting specifies the maximum number of domain values that should be provided to the AI model as options to select from. The default value is 50. This ensures optimal performance by limiting the number of choices the model must consider. This is a required field.

#### Input Attributes (Context) Section

The Input Attributes section allows you to select one or more entity attributes that should be provided to the AI model as context. These attributes help the model make informed decisions about what content to generate for the enrichment attribute.

The interface displays all available attributes from your entity in a list format with checkboxes. The attributes are organized as follows:

* **Name** and **Code** appear first (if available)
* All other attributes are listed alphabetically below

To select input attributes:

1. Review the list of available Product Attributes.
2. Check the box next to each attribute you want to provide as context to the AI model.
3. Use the **Select** column header to see your selections.

Choose attributes that are most likely to contain relevant information for generating the enriched value. For example, if enriching a Marketing Description attribute, you might select Name, Code, Color, Component, and Category as input attributes.

The more relevant context you provide, the better the AI model can generate appropriate content. However, focus on attributes that truly contribute meaningful information rather than selecting all available attributes.

### Run Options Tab

The Run Options tab determines how and when the agent executes. The tab contains an **Execution** section where you configure trigger conditions.

Unlike the Data Quality Agent, the Enrichment Agent does not require records to be invalid to run. You can configure it to run when records are added, when records are updated, or both.

* **Run-as user**: Select the user account that will be used to make changes when the agent is triggered.
* **Trigger when records are added**: Check this box to cause the agent to run any time records are added to the entity.
* **Added records filter**: Click to create an expression that limits the trigger to run only when the records added meet certain criteria (e.g., when the enrichment attribute is empty).
* **Trigger when records are updated**: Check this box to cause the agent to run any time records in the entity are updated.
* **Updated records filter**: Click to create an expression that limits the trigger to run only when the records edited meet certain criteria (e.g., when source attributes change).

It is recommended to use filters to control when enrichment occurs. For example, you might only want to enrich the Marketing Description when it's empty, or re-enrich it when the product's Features attribute changes.

### Scheduling Tab

The Scheduling tab allows you to define optional schedule expressions that control when the agent executes. This provides an alternative to trigger-based execution if you prefer to run the agent at specific times or intervals.

The Scheduling tab displays a **Run Schedules** section with a grid where you can add multiple schedules. Each schedule consists of three components:

* **Name**: Enter a descriptive name for the schedule (e.g., "Schedule 1", "Nightly Enrichment")
* **Schedule**: Enter a Cron expression that defines when the agent should run
* **Records Filter**: Optionally click to create an expression that limits which records the agent processes during this scheduled run

To add a new schedule:

1. Click the **+** button in the Run Schedules header.
2. Enter a name for the schedule in the **Name** column.
3. Enter a Cron expression in the **Schedule** column.
4. Optionally, click in the **Records Filter** column to create a filter expression.

You can add multiple schedules to run the agent at different times or with different record filters. Use the **Clear All** link to remove all schedules at once.

If no schedules are configured, the agent will run based on the execution mode selected in the Run Options tab (trigger-based execution).

Example scheduling expressions (Cron format):

* **0 0 \* \* \***: Run daily at midnight
* **0 \*/6 \* \* \***: Run every 6 hours
* **0 0 \* \* 1**: Run weekly on Mondays at midnight
* **0 2 \* \* \***: Run nightly at 2 AM
* **0 0 1 \* \***: Run monthly on the first day at midnight

## Saving Your Agent

After configuring your agent across all tabs, use the buttons at the bottom of the configuration form to save your work. These buttons are available on every tab:

* **Save**: Saves your changes and keeps the agent configuration form open for further editing
* **Save and Close**: Saves your changes and returns you to the Agents grid
* **Close**: Closes the form without saving any changes made since the last save

---

## Example Use Cases

### Product Marketing Descriptions

* **Attribute to Enrich**: Marketing Description
* **Agent Prompt**: "Generate a compelling 2-3 sentence marketing description that highlights the product's key features and benefits"
* **Input Attributes**: Name, Code, Features, Category, Color
* **DBA Record Limit**: N/A (not a domain-based attribute)

### Company Website Discovery

* **Attribute to Enrich**: Website
* **Agent Prompt**: "Use the company name and address to find the company's official website URL"
* **Input Attributes**: Name, Address, Industry, Country
* **DBA Record Limit**: N/A (not a domain-based attribute)

### Account Classification

* **Attribute to Enrich**: Account Tier (domain-based attribute)
* **Agent Prompt**: "Based on the account's annual revenue, employee count, and industry, classify into the appropriate tier"
* **Input Attributes**: Name, Annual Revenue, Employee Count, Industry, Country
* **DBA Record Limit**: 50 (provides up to 50 tier options to the AI model)

### Product Categorization

* **Attribute to Enrich**: Product Category (domain-based attribute)
* **Agent Prompt**: "Analyze the product name and description to assign the most appropriate category"
* **Input Attributes**: Name, Code, Component, Color, B2BCompany
* **DBA Record Limit**: 50 (provides up to 50 category options to the AI model)

---