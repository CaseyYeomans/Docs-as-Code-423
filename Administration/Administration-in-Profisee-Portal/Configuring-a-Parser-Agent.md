# Configuring a Parser Agent

The Aisey Parser Agent automatically structures unstructured data by using AI to extract meaningful information to populate attributes. This agent is designed to process large volumes of unstructured text data—such as product descriptions, notes, or document content—and intelligently map the extracted information to structured fields in your entity. The agent runs as a specified run-as user and will autonomously perform data parsing and mapping tasks based on the triggers and schedules you configure.

### Overview Tab

The Overview tab displays the basic agent configuration in a **Provider Details** section. You can review and edit the following information:

* **Strategy Name**: The name given for the agent (editable, required)
* **Agent Type**: Displays "Parser Agent" (read-only)
* **Configuration \***: The previously configured model (Hyperlink) used by this agent (editable dropdown, required)
* **Entity**: The entity this agent operates on (read-only)

### Structure Data Tab

The Structure Data tab is where you configure how the agent identifies unstructured data and which entity attributes should be populated from that data. This tab is divided into two main sections: **Source** and **Assignment Selection**.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i42d0ffd2dc9ae27b.png)

#### Source Section

The Source section defines where the unstructured data is located and provides context for the AI parser.

**Unstructured Data Location**

Select the attribute within your entity that contains the unstructured text data you want to parse. This could be a large text field containing product descriptions, notes, comments, or any other unstructured content. Use the **Type to search** dropdown to locate the appropriate attribute.

For example, if you have a *Product Description* attribute that contains paragraphs of text about each product, you would select this as your Unstructured Data Location.

**Agent Prompt**

Enter clear instructions to help the AI understand what information to extract from the unstructured data and how to structure it. The prompt provides context that guides the model in identifying and extracting relevant information for mapping to your entity attributes.

Examples of effective prompts:

* "Extract product specifications, features, and categorization information from the description text."
* "Parse the notes field to identify key account details including industry, location, and contact information."
* "Analyze the product description to extract color, material, dimensions, and manufacturer details."
* "From the unstructured text, identify and extract relevant product attributes such as category, pricing tier, and target market."

The quality of the parsing depends on how well you define this prompt. Be specific about what types of information should be extracted and how they relate to your entity attributes.

**DBA Record Limit**

When the agent needs to populate domain-based attributes, specify the maximum number of domain values that should be provided to the AI model as options to select from. The default value is 50. This ensures optimal performance by limiting the number of choices the model must consider when mapping data.

#### Assignment Selection Section

The Assignment Selection section allows you to control which entity attributes the AI should populate from the unstructured data. This gives you granular control over the parsing process.

The interface displays all available attributes from your entity in a two-column format:

* **[Entity] Attribute** (or your entity name + "Attribute"): Lists all attributes in the entity
* **Assign**: Checkboxes to select which attributes the AI should attempt to populate

To configure assignment selection:

1. Review the list of available attributes in the left column.
2. Check the box in the **Assign** column for each attribute you want the AI to populate from the unstructured data.
3. Leave unchecked any attributes that should not be populated by the parser.

You don't need to select all attributes. Choose only those attributes where the unstructured data is likely to contain relevant information. This improves parsing accuracy and reduces processing time.  
  
For example; if parsing product descriptions, you might check boxes for attributes like Name, Color, Component, Country, and DaysToManufacture, while leaving technical fields or system fields unchecked.

### Run Options Tab

The Run Options tab determines how and when the agent executes. The tab contains an **Execution** section where you configure trigger conditions.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ia88dab5bac3f37bb.png)

* **Run-as user**: Select the user account that will be used to make changes when the agent is triggered.
* **Trigger when records are added**: Check this box to cause the agent to run any time records are added to the entity.
* **Added records filter**: Click to create an expression that limits the trigger to run only when the records added meet certain criteria (e.g., when the unstructured data location attribute is populated).
* **Trigger when records are updated**: Check this box to cause the agent to run any time records in the entity are updated.
* **Updated records filter**: Click to create an expression that limits the trigger to run only when the records edited meet certain criteria (e.g., when the unstructured data location attribute changes).

Use filters to ensure the parser only runs when there is unstructured data to process. For example; trigger only when the Unstructured Data Location attribute is not empty, or when it has been modified.

### Scheduling Tab

The Scheduling tab allows you to define optional schedule expressions that control when the agent executes. This provides an alternative to trigger-based execution if you prefer to run the agent at specific times or intervals.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i4ed37b8b3c9cb64f.png)

The Scheduling tab displays a **Run Schedules** section with a grid where you can add multiple schedules. Each schedule consists of three components:

* **Name**: Enter a descriptive name for the schedule (e.g., "Schedule 1", "Nightly Parsing")
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
* **0 3 \* \* \***: Run nightly at 3 AM
* **0 0 1 \* \***: Run monthly on the first day at midnight

## Saving Your Agent

After configuring your agent across all tabs, use the buttons at the bottom of the configuration form to save your work. These buttons are available on every tab:

* **Save**: Saves your changes and keeps the agent configuration form open for further editing
* **Save and Close**: Saves your changes and returns you to the Agents grid
* **Close**: Closes the form without saving any changes made since the last save

---

## Example Use Cases

### Product Specification Extraction

* **Unstructured Data Location**: Product Description (long text field)
* **Agent Prompt**: "Extract product specifications including color, material, country of origin, and manufacturing time from the description text"
* **Assignment Selection**: Color, Component, Country, DaysToManufacture
* **DBA Record Limit**: 50
* **Example Input**: "This premium bicycle features a lightweight aluminum frame in vibrant red. Manufactured in Taiwan with precision engineering. Ships within 10-14 business days."
* **Expected Output**: Color → "Red", Component → "Aluminum", Country → "Taiwan", DaysToManufacture → "14"

### Customer Account Details Parsing

* **Unstructured Data Location**: Account Notes
* **Agent Prompt**: "Parse account notes to identify industry classification, geographic location, company size, and primary contact details"
* **Assignment Selection**: Industry, Country, EmployeeCount, ContactName, ContactEmail
* **DBA Record Limit**: 50

### Inventory Item Categorization

* **Unstructured Data Location**: Item Description
* **Agent Prompt**: "Analyze the item description to determine appropriate category, subcategory, and key attributes like brand and model"
* **Assignment Selection**: Category (DBA), Subcategory (DBA), Brand, ModelNumber
* **DBA Record Limit**: 50 (for categories and subcategories)

### Service Request Detail Extraction

* **Unstructured Data Location**: Request Details (free-form text)
* **Agent Prompt**: "Extract key information from service requests including priority level, service type, affected product, and estimated resolution time"
* **Assignment Selection**: Priority (DBA), ServiceType (DBA), AffectedProduct, EstimatedResolutionDays
* **DBA Record Limit**: 50

---

## Understanding Parser vs. Enrichment Agents

While both Parser and Enrichment agents use AI to populate attributes, they serve different purposes:

| Feature | Parser Agent | Enrichment Agent |
| --- | --- | --- |
| **Purpose** | Extract and structure data from unstructured text | Generate new content or populate single fields |
| **Input** | Unstructured text within the entity | Multiple structured attributes as context |
| **Output** | Multiple populated attributes | Single enriched attribute |
| **Use Case** | Parsing product descriptions into specifications | Generating marketing copy from product specs |
| **Data Source** | One unstructured attribute | Many structured attributes |

Choose the Parser Agent when you have unstructured text that needs to be broken down into multiple structured fields. Choose the Enrichment Agent when you have structured data and need to generate new content or populate a single field.

---