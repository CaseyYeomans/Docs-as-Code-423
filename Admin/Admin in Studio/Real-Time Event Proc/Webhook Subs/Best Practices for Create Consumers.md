# Best Practices for Creating Consumers

Beyond the authentication of the bearer token, the **Webhook Consumer** has the responsibility to return a response to the Webhook Subscriber indicating whether it was successful in processing the event. Generally speaking, Profisee recommends issuing a 200 response code indicating that the event was received and processed properly. Otherwise, an error response code should be returned along with textual details that can be captured and logged to Profisee's logging system. In addition, ensure consumers adhere to the following best practices for painless user experience.

- Ensure status responses are returned at the beginning of any processes. Webhook Consumers should not perform long-running processes directly on the main thread that receives the event. Consumers should return status responses quickly.
- Each Webhook Consumer should be responsible for its own resiliency by building in queuing and retry capabilities that ensure that events are not dropped or lost due to transient failures during operations.
- Use [standard response codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) that developers are familiar with.
- Refer to the [**Webhook** **Consumer Template**](http://github.com/Profisee/webhooktemplate) provided in the Profisee GitHub for an example of an ideal consumer.