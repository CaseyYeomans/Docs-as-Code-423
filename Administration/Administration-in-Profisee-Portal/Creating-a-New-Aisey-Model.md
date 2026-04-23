# Creating a New Aisey Model

You can create new Aisey models from the **Models** tab under the **Aisey** section in the administration area of Profisee Portal. Aisey models represent AI model configurations (Azure OpenAI deployments) that power Aisey features throughout the platform. Each model can be configured for specific AI capabilities such as embeddings or chat completion.

To create a new model:

1. Navigate to the **Models** tab under the **Aisey** section in Administration.
2. Click the **+** icon in the toolbar. A slide-out form opens from the right side of the screen.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i27f382e5e3c3dac9.png)
3. Complete the following required fields in the **Model Details** section:
   * **Model Name**: Enter a descriptive name for your model.
   * **Model Type**: Select the type of AI capability this model provides from the dropdown menu. Available options include:
     + **Embeddings**: For models that generate vector embeddings from text
     + **Chat Completion**: For conversational AI and text generation models
     + See *Understanding Model Types* below for more information.
   * **Endpoint URL**: Enter the Azure OpenAI endpoint URL for this model deployment.
     + If the model is an **Embeddings** model, this will be a deployment URL found in the Azure Foundry Portal.
   * **Key**: Enter the authentication key for accessing the Azure OpenAI service. This field is displayed as a password field for security. Clicking this field opens the Credentials window.
     + **Name**: The given name for your API Key
     + **Vault Type**: Local Vault or Azure Key Vault
4. Click the **Test Connection** button to verify that your endpoint URL and key are valid and that the model is accessible. A success or error message will be displayed based on the validation results.
5. Click **Save** or **Save and Close** to create the model.

Only administrators with both **AI** and **Connect** licenses can access the **Models** tab and create or edit models.

## Editing an Existing Model

To edit an existing model, you can either click on the model name in the grid or right-click the model row and select **Open** from the context menu. The slide-out form opens with all existing model details pre-populated.

You can update any of the following fields:

* **Model Name**: Change the descriptive name
* **Model Type**: Switch between Embeddings and Chat Completion
* **Endpoint URL**: Update the Azure OpenAI endpoint
* **Key**: Replace the authentication key

After making changes, use the **Test Connection** button to verify the updated configuration, then click **Save** or **Save and Close** to apply your changes. The grid will update automatically to reflect the modifications.

Embeddings models cannot have their Name edited to prevent issues with AI Matching.

## Deleting a Model

To delete one or more models, right-click on a model row (or select multiple rows) and choose **Delete** from the context menu. A confirmation dialog will appear with the title "Delete Model(s)" and the message "Are you sure you want to delete these Model(s)?"

Click **Confirm** to permanently delete the selected models, or **Cancel** to close the dialog without making changes.

Deleting a model that is currently in use by Aisey agents may prevent those agents from functioning properly. Ensure no agents are dependent on the model before deleting it.



## Understanding Model Types

### Embeddings

Embeddings models convert text into numerical vectors that capture semantic meaning. These models are used for:

* Semantic search and similarity matching
* Document clustering and classification
* Finding related records based on meaning rather than exact text matches

### Chat Completion

Chat Completion models generate human-like text responses based on input prompts. These models are used for:

* Data quality remediation (automatically filling missing values)
* Parsing and structuring unstructured data
* Enriching records with contextual information
* Generating descriptions or summaries

## Model Configuration Best Practices

When configuring Aisey models, consider the following recommendations:

* **Descriptive Names**: Use clear, descriptive names that indicate the model's purpose or capabilities (e.g., "GPT-4 Chat" or "Ada Embeddings").
* **Model Type Selection**: Choose the correct model type based on your Azure OpenAI deployment. Embeddings models are used for similarity search and semantic analysis, while Chat Completion models are used for conversational AI and text generation.
* **Test Before Saving**: Always use the Test Connection button before saving a new model to ensure your credentials and endpoint are configured correctly.
* **Secure Key Management**: Keep your Azure OpenAI keys secure. The key field is masked in the interface for security, but administrators should follow organizational security policies for key rotation and access control.
* **Multiple Models**: You can configure multiple models for different use cases. For example, you might have one model optimized for embeddings and another for chat completion tasks.

---