# Aisey FAQ

- What sources of knowledge does Aisey draw from when answering questions?

As of the 2025.R3 release, Aisey draws from the Profisee Wiki, Release Notes, and the REST API Swagger page as the source for all the information it gives in response to questions.

- Can Aisey give information about a version of the product other than the one I'm using?

No. To prevent distributing incorrect information, Aisey will only give answers relevant to the version of the product currently in use.

- Will changes made by Aisey be visible in the transaction history of a record?

Changes made by Aisey are logged in the transaction history as the user that ran the request through Aisey, and are not specified as a change made by AI.

- Is there a way to view a history of changes made by Aisey specifically?

There is not currently a way to view a list of changes made by Aisey.

- Can Aisey generate an Excel file for an entity?

No, but it can navigate you to the Data Browser where you can export an entity as an Excel spreadsheet.

- How long is Aisey chat history available?

Readable chat history with Aisey is only maintained for your browser session, and it disappears whenever the browser is closed or refreshed. However, the chat is cached for 30 minutes, allowing Aisey to "remember" recent interactions.

- Can my chats or prompts be seen by anyone else?

No other Profisee users, including super administrations, can see a user's chat history with Aisey.

- What does it mean if I get the error message, "I am sorry, I have exceeded my token rate limit. Please try again in a moment."?

Token rate limit refers to the maximum number of tokens (units of text) that can be processed within a certain timeframe. If a user or application sends too many requests or processes too much text too quickly, the system temporarily blocks further requests to prevent overload.
This message is a throttle warning, not an error. It is asking you to wait a bit before trying again. Usually this message appears in the chatbot because the user is sending too many requests in a short time or their input or output is very long. The exact limit for tokens differs by the model that is being used. If you want to adjust this, you can edit the Model Quota or Deployments tab in AzureAI Foundry Portal.