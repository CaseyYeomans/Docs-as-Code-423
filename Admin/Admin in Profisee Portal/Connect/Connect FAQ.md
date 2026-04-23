# Connect FAQ

- Can we configure Connect strategies to be event-triggered?

Yes, strategies can be triggered by data changes and scheduled and on-demand data flows.

Connect is easier to configure than Real-Time Event Processing and offers additional options for triggering. Connect is the recommended approach.

- What is the difference between the Webhook Subscriber (Real-Time Event Processing) and the Webhook Service Provider (Connect)?

Connect provides a **streamlined, no-code solution** for connecting to webhooks without setting up Real-Time Event Processing scenarios.

- I saw a warning message logged to the *logging.tSystemLog* table by Connect (assemblyname =Profisee.Platform.Services.ConnEx.Api) that said "No records were published." What does this mean?

There are two scenarios that could cause this error to occur:

1) The output attributes on the connect strategy were not configured correctly. An administrator should confirm the strategy works as expected for one record.

2) The strategy ran, but there was nothing to do. As an example, an OpenAI strategy that parses unstructured data might have been triggered, but there was no unstructured data to act against, so no change was published.