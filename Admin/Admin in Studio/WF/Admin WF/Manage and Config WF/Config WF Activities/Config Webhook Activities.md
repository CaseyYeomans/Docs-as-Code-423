# Configuring Webhook Activities

The Webhook activity allows users to inject custom code by directing the workflow to an existing web service with an endpoint the workflow can access.

To configure a Webhook activity:

1. Open the [Workflow Configuration](https://support.profisee.com/wikis/profiseeplatform/configuring_workflows) window for a registered workflow.
2. Navigate to the **Details** tab.
3. Select the Webhook activity you want to configure.

#### Activity Field

The activity field displays the version of Profisee FastApps Studio in which the workflow was created. If the workflow was imported from a different version than the version of Profisee you are running, the workflow process may encounter errors. If the Assembly Version is a higher version than the instance of Profisee you are running, it is recommended you upgrade the platform before continuing.

If desired, a user can add a description to the task that will be displayed to the workflow participants in their notifications.

#### Webhook Field

4. Input the **Endpoint URL**to which this activity points its request for external processing.

5. Select a value for **Retry Delay**.This value determines the number of seconds the Webhook activity will delay before retrying a call. If this value is set to 0, no retries are attempted.
6. Select a value for **Retry Limit**. This value determines the number of attempts the Webhook will make to retry a call before it no longer attempts to throw an exception. If this value is set to 0, no retries are attempted.