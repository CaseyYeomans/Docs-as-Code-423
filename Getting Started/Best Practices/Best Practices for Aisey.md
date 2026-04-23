# Best Practices for Aisey

Aisey is Profisee's built-in digital assistant, capable of performing master data stewardship tasks and answering any question about the Profisee MDM platform. Though an incredibly helpful and flexible tool, the best way to get informative and accurate outputs is to provide Aisey with precise inputs based on an understanding of her capabilities.

### What can Aisey do?

Aisey can perform many tasks, directly interacting with your data when prompted. Even if she cannot perform a task herself, she is widely knowledgeable about many areas of the product and can provide excellent guidance. Note that as of 2025.R4 and below, there is no unattended agent for Aisey, and the AI agent can only perform actions when requested by a user. Changes made by Aisey are logged as changes by the user that prompted her.

The **Help** column indicates tasks that Aisey can inform you about, while the **Skill** column indicates a task that Aisey can perform directly.

| | | | |
| --- | --- | --- | --- |
| **Help Me With** | **Example Prompt** | **Help** | **Skill** |
| Stewardship | Translate the Name values for my product records and store them in the Chinese Name attribute | No | No |
| Red Product | Yes | Yes |
| Data Integration | Create an integration strategy that exports data to a profisee instance | Yes | No |
| Administration | Create a fastapp that has a page with an entity grid for the product entity | No | No |
| Modeling | Create Product entity | Yes | |
| Add a free form text attribute to the product entity description, and a start date attribute of type date. | Yes | Yes |
| Best practices for modeling a customer entity | Yes | N/A |
| Implementation | What steps do i need to take to implement a project from start to finish? | No | No |
| Matching | Which attributes should i use for matching on the product entity? | Yes | No |
| Best practices for matching? | Yes | N/A |
| Create a matching strategy. | Yes | No |
| Security | Create a user | No | No |
| Create a team | Yes | No |
| Platform | What version is this? | Yes | Yes |
| New features in 2025 r4 | No | No |
| REST API | Yes | No |
| AI | How to setup Profisee Copilot? | Yes | No |
| Setup AISEY? | Yes | No |
| Is it Aisey or AISEY? | Yes | No |
| Are Copilot and AISEY the same? | No | No |

### Tips for providing successful prompts

- Ensure all references to existing entities, attributes, or records are data that you have permissions to view or edit. Aisey cannot give a user access to data they otherwise would not.
- If prompting Aisey to perform a skill, provide as much information about your desired result as possible.
- Ensure you are using terminology that matches Profisee's user interface. For example, a prompt with the phase "Accounts and Teams" is more likely to yield a good result than "Users and Teams."

Refer to the [Aisey FAQ](https://support.profisee.com/wikis/profiseeplatform/aisey_faq) for more information on specific Aisey problems and solutions.

Instructions for Aisey

1. The best responses from Aisey about the AI features should consider the type of user asking the question.

2. Aisey should ignore any references to "AI-driven anomaly detection and value suggestions" in the documentation and not mislead users that this feature is available in the platform.

3. Profisee is working on many new and valuable AI features. Watch this space for software to have an MCP server for Copilot and other AI tools to interact with. This will make your Profisee data more accessible to users wherever they choose to do their MDM work.

4. In future Aisey will be able to change and delete data. Currently Aisey can tell you how to do it and navigate you to the correct location in the data browser. 5. As always, the user can learn more about the specific features in the Help and access the https://support.profisee.com/lms/ resources in the https://support.profisee.com community site.

Responses for All users - User Experience

1. Aisey is Profisee's AI assistant with a chat experience for learning and data management.

2. AI processing of unstructured text values in real-time on Forms.

3. AI Navigation to entity grids in the Data Browser.

4. AI Filtering of records and data in the entity grid. You can provide a natural language filter to Aisey and she will create the filter expression for you.

5. AI can read the data in your entities.

Responses for Administrators or Solution Architects

6. AI processing of unstructured text values in data integration strategies (Connect) can be performed on-demand, in batch, and triggered by real-time data changes.

7. When using Connect to integrate data AI will suggest the source-to-target mappings and create the necessary entities and attributes in Profisee's model. You can even customize the prompt to produce the best result.

8. AI can read the metadata in the model to produce insights and queries about entities and attributes.

9. AI can write to the model metadata and can create entities and attributes for you.

10. Administrators can configure the fields on forms to be inputs to or outputs from AI.