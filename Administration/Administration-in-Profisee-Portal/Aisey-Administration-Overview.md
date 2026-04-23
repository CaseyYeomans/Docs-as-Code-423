# Aisey Administration Overview

Profisee administrators can manage Aisey configurations in Profisee Portal through the **Aisey** section in the administration area. Aisey is Profisee's AI assistant that powers intelligent data management capabilities, including parsing unstructured data, automatically fixing data quality issues, and enriching records with contextual information.

The Aisey administration area is organized into three main tabs: **Settings**, **Models**, and **Agents**, providing centralized management for all AI-powered features in the platform.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i908e1391c1c80bd.png)

## Aisey Settings

The **Aisey Settings** tab provides system-level configuration for connecting to Azure OpenAI services. From here, you can enter your Azure OpenAI endpoint URL and authentication key, then test the connection to verify your credentials are working correctly. You can also use the DBA Context Limit setting to determine the maximum number of usable DBA values sent to the prompt (Minimum 1).

This settings tab impacts the Aisey chatbox experience and OpenAI  configuration, but does not impact Aisey models or Agents. See **Models** and **Agents** below for more information.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ie9b422e3beb9daad.png)

## Models

The Models tab serves as a centralized area to manage all AI model configurations that power Aisey agent and AI Matching features. This tab allows you to configure multiple models for different purposes.

From here, a list of all configured Models is displayed with the following information:

* **Name**: The name given for the Model
* **Type**: The AI service provider (currently Azure AI for all models)
* **Endpoint URL**: The Azure OpenAI endpoint URL for this model
* **Key**: The key for the above endpoint.

To add a new model, click the **+** button at the top of the grid. A slide-out form will appear where you can enter the model name, endpoint URL, and authentication key. Use the **Test Connection** button to verify your credentials before saving.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibbc82e032ef975aa.png)

## Agents

Agents are specialized AI workflows that perform specific tasks such as parsing unstructured data, fixing data quality issues, or enriching records with additional information. Agents run as a specified user and have the ability to automatically perform data management tasks.

From here, a list of all created Agents is displayed with the following information:

* **Agent Name**: The name given for the Agent
* **Agent Type**: The type of AI agent (Aisey Parser Agent, Aisey Data Quality Agent, or Enrichment Agent)
* **Model**: The Aisey Model to be used for this agent
* **Entity**: The entity the agent operates within

If desired, you can right-click an agent (or select multiple) in this list to bring up the context menu, allowing you to **Open**, **Clone**, **Run**, or **Delete** the selected agents. The **Open**, **Clone**, and **Run** options are only available when selecting a single agent.

---