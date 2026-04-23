# OpenAI

The table below displays options and functions for OpenAI in System Settings.

| Option | Function |
| --- | --- |
| OpenAI Key | Your Azure OpenAI API Key |
| DBA List Context Limit | The maximum number of usable DBA values sent to the prompt (Minimum 1) |
| OpenAI Endpoint | The URL for your Azure OpenAI Endpoint\* |

An Azure account with OpenAI capabilities is required to use these settings. Refer to the [Azure Support Site](https://azure.microsoft.com/en-us/products/ai-services/openai-service) for more information on obtaining your OpenAI API Key and OpenAI Endpoint.

\*Note that the endpoint for the completion is different than the endpoint listed on the Open AI service overview page. To obtain this endpoint:

1. Open your **Open AI Service**in the Azure portal.
2. Open the **Azure Open AI Studio** to deploy a model.
3. Create a new deployment.
4. Navigate to the **Completions**list (also called the **Completions Playground**).
5. Click **View Code**to see the **Completion Endpoint** and **Key** values.