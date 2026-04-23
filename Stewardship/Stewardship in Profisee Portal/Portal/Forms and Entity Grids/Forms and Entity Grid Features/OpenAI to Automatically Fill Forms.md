# Using OpenAI to Automatically Fill Forms

Forms that have been [configured for OpenAI](https://support.profisee.com/wikis/profiseeplatform/field_control) automatically populate records with suggestions based on input data in your form. Forms can be configured for OpenAI through Profisee FastApp Studio, or within Profisee Portal by a user with administrative privileges.

When configured this way, fields within a form will function as Inputs or Outputs depending on configuration. **Input fields**provide contextual information to the OpenAI algorithm and will not receive suggestions from the AI. **Output Fields** do not provide information for the OpenAI algorithm and will receive suggestions from the AI.

Once configured, OpenAI will make suggestions in two ways:

- Output Fields with no manually-input data may be automatically populated with an OpenAI suggestion. In this case, the field is highlighted in blue. Inputting data into an Input Field may cause the AI algorithm to begin populating relevant empty Output Fields. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iaf4db6fb5f30767f.png)
- Output Fields with manually-input data may have an OpenAI icon hovering above the entry. This icon can be clicked to replace the manually-input data with the AI-generated suggestion. If the suggestion is not relevant, you can click the Trash icon to disregard it. Inputting data into an Input Field may cause the AI algorithm to begin suggesting changes to relevant Output Fields.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic24bac8fda8fd937.png)