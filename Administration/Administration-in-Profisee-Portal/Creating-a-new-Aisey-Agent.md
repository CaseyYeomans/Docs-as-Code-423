# Creating a new Aisey Agent

You can create new Aisey agents from the **Agents** tab under the **Aisey** section in the administration area of Profisee Portal. Aisey agents are AI-powered automation workflows that perform specific tasks such as parsing unstructured data, automatically fixing data quality issues, or enriching records with contextual information.

To create a new agent:

1. Navigate to the **Agents** tab under the **Aisey** section in Administration.
2. Click the **+** icon in the toolbar. The **Create a New Agent** dialog opens.  
   ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iccaadf1e1965836b.png)
3. Complete the following required fields:
   * **Agent Name**: Enter a descriptive, unique name for your agent.
   * **Agent Type**: Select the type of agent to create from the dropdown:
     + **Aisey Parser Agent**: Structures unstructured data by extracting information from text or documents
     + **Aisey Data Quality Agent**: Automatically fixes missing or invalid attribute values using contextual information
     + **Enrichment Agent**: Enhances records with additional information from external sources
   * **Model**: Select which configured AI model the agent should use. Only Chat Completion models are available (Embedding models are not shown).
   * **Entity**: Specify the entity the agent will operate on.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-icbd8a8d22345af02.png)
4. Click **Continue** to open the agent configuration form. The configuration experience will adapt based on the selected Agent Type.



---

### See more

* [Data Enrichment Agent](https://support.profisee.com/wikis/profiseeplatform/configuring_an_enrichment_agent)
* [Data Quality Agent](https://support.profisee.com/wikis/profiseeplatform/configuring_a_data_quality_agent)
* [Parser Agent](https://support.profisee.com/wikis/profiseeplatform/configuring_a_parser_agent)