# Configuring Webhooks

Before you can post Webhook events, you must register the **Webhook Subscriber**. This process includes the following steps:

1. Create one or more user accounts that will be associated with the Webhook Consumers you and your team have created.
2. Register the Webhook Subscriber.
3. Create Subscriber Configurations for each distinct Webhook Consumer endpoint.
4. Create Internal Event Scenarios associated with the Subscriber Configurations that determine the events that should be directed to the Webhook Consumers.

## Creating Webhook User Accounts

User accounts are required to authenticate Webhook events received by a Webhook consumer. An administrator must create at least one user account to associate with the Webhook Consumer Process. All user accounts configured for Webhook subscribers musthave **Unattended Authentication** enabled.

To create a User Account:

1. [Create](https://support.profisee.com/wikis/profiseeplatform/add_accounts) a new Profisee account, or [Edit](https://support.profisee.com/wikis/profiseeplatform/edit_accounts) an existing one.
2. Ensure the **Unattended Authentication** option is enabled.
3. Record the User Name generated for this account.

You may or may not want to create several accounts, depending on your environment and preferences. A single account can be shared across multiple Webhook Consumers, or a new account can be used for each individual Webhook Consumer. Creating several accounts allows each Webhook Consumer to be more tightly controlled in terms of what data it can access. Sharing the same account across many Webhook Consumers means that all consumers will have broad access to data needed by every consumer.

## Registering the Webhook Subscriber

The Profisee **Webhook Subscriber** initiates workflows based on created, updated, or deleted data. Before you can invoke a Webhook Consumer, you must first register the Webhook Subscriber. The Webhook Subscriber is installed when the Profisee server is installed on a node in your cluster.

To register the Webhook Subscriber in Profisee:

1. In the navigation panel, click **Real-Time Event Processing**, under Administration.
2. On the Real-Time Event Processing tab, click **Subscribers**.

The Subscriber registration tab displays.

3. Select the Webhook Subscriber in the **Available Subscribers** pane.

The subscribers listed in this panel are the subscribers installed on all event consuming servers in the cluster.
If the Webhook Subscriber does not appear in the list, contact Customer Support to make sure it has been installed properly.

1. Click the right arrow to add the subscriber to the Registered Subscribers column.
2. Click **Save** or **Save and Close** to save the registered subscriber.

## Creating Webhook Subscriber Configurations and Event Scenarios

Once you have all desired Webhook accounts, you can configure a Webhook subscriber in FastApp Studio.

1. Open Profisee FastApp Studio.
2. Navigate to the **Real Time Event Processing** tab.
3. Open the **Subscriber Configuration**.
4. Give your Subscriber Configuration a unique name.
5. Click the **Properties** tab and add values for the following **General** properties.

- **URL**: This contains the REST endpoint that will be called with the POST operation when a subscribed data change event occurs.
**NOTE**: The consumer's configuration (i.e., **appconfig.json** file) must use this same endpoint when configuring authentication authentication during the web application startup process.
- **Run-as User**: Specify the user account name that will be used to generate a bearer token that will be sent with the webhook post to allow the webhook authenticate that the post came from a valid Profisee instance. Additionally, the Webhook Consumer can use this bearer token to authenticate back to the Profisee server to perform any necessary service operations permitted for this user.
- **Retry Status Codes**: A comma-separated list of [HTTP status codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) that will be retried by the Webhook Subscriber when received.
- **Severe Error Status Codes**: A comma-separated list of [HTTP status codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) that should be interpreted by the Webhook Subscriber as a severe error that should cause the associated Subscriber Configuration to be unloaded and the events to stop flowing.
- **Include Authorization Header**: A true/false option select that allows you to provide a Profisee Auth token in the Authorization Header.
- **Additional Headers**: Allows headers in .json format to be uploaded as additional headers.

## Creating Internal Event Scenarios associated with Your Subscriber Configurations

Once a subscriber configuration has been created, one or more event scenarios can be created to focus events on the specific types of data changes that are of interest to your Webhook Consumers. Follow the steps outlined in [Create an Internal Event Scenario](https://support.profisee.com/wikis/profiseeplatform/create_an_internal_event_scenario) to complete your webhook configuration.