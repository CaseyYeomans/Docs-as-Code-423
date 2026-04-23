# Webhook

The Webhook activity is a standard component of Profisee's workflow activities delivered via the SDK. The Webhook activity allows the Profisee platform to invoke custom code that runs outside the platform. The Webhook Activity sends a payload in the form of a dictionary of name/value pairs to the webhook which can process the data and return the results to the workflow in a response dictionary.

The webhook activity takes the following arguments as input:

| | | |
| --- | --- | --- |
| **In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| **RequestPayload** | Dictionary<string,object> | This InArgument represents the payload of message to the webhook consumer. The content of the RequestPayload argument is completely at the discretion of the workflow designer and webhook consumer. |
| **Out Arguments** | | |
| **ProcessingStatus** | int | Indicates the processing status of the request made to the webhook consumer. |
| **ResponsePayload** | Dictionary<string,object> | This Out Argument represents the payload of message returned from the webhook consumer |

### Remarks

The webhook activity configuration contains the REST endpoint URL to which the webhook activity will post its external processing request. Refer to [this article](https://support.profisee.com/wikis/profiseeplatform/configuring_webhook_activities) for more information on configuring Webhook activities in FastApp studio.

###