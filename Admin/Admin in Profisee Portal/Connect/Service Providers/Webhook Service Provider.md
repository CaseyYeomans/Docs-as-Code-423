# Using the Webhook Service Provider

The **Webhooks** service provider allows Profisee administrators to connect and interact with custom Webhooks, allowing for a wide variety of custom functions. This service provider provides a streamlined, no-code solution, making it an accessible alternative to connecting to webhooks via real-time event processing.

# Adding a New Webhook Service Configuration

When adding a new service configuration for this service provider, you must configure it with the following settings:

- **Webhook URL**: The URL to be used for the webhook consumer.
- **Configuration Name**: The user-defined name for this configuration.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ib7bc8e54fc852989.png)

When finished, click Confirm to create the service configuration.

## Webhook Configuration

Once created, you must configure the following options on the Overview and Settings tabs.

### Overview

The Overview section allows you to view the configuration name, service provider, and webhook URL previously configured. Of these, only the configuration name can be edited.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i58977e1f3f9fe925.png)

### Settings

Configure the following settings for this service configuration:![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i2b1e2b78767f84cd.png)

#### Settings

- **Include Profisee Token**: Check to create a Profisee Authentication Token that is included in the payload sent to the webhook.
- **OAuth URL**: The URL for your OAuth credentials.
- **OAuth Client ID**: The Client ID for your OAuth account.
- **OAuth Client Secret**: The secret for your OAuth account.
- **OAuth Scope**: The specific level of access for your OAuth account.

#### Request Headers

Input user-defined key/value pairs to specify the function of the webhook. You can click the + icon to add additional keys to the request header. This can be specified for all strategies running this configuration, or can be configured per-strategy. Key/Value pairs can be input as text or as expressions.

#### Request Query String

- **Key**: The parameter name
- **Value**: The value for this parameter

You can click the + icon to add additional key/value pairs to the request query string.

# Creating a new Strategy using the Webhook Service Configuration

## Adding a New Webhook Strategy

When adding a new integration strategy using a Webhook-based Server Configuration, the strategy gains no new options beyond the standard Integration Strategy Options.

1. Navigate to the **Strategies** window under the **Connect** tab.
2. Click the **+** icon to add a new strategy.
3. Provide a name for your strategy under the **Strategy Name** field.
4. Select the Webhook-based service configuration created previously from the **Service Configuration** dropdown.
5. Select an Entity from the **Entity** dropdown menu, or create a new entity by clicking the **+** icon.
6. Click **Continue**. The Strategy editor is created on the page. If you do not wish to continue editing this strategy, click **Save** or **Save and** **Close**.

## Configuring the Strategy

Once the Strategy is created, complete the settings on the following tabs.

### Overview

The Overview tab allows you to view the previously configured Strategy Name, Configuration, and Entity. Of these, only the Strategy Name can be edited.

### Request

#### Request Body

- **Key**: The parameter name
- **Value**: The value for this parameter

#### Request Body.Records

- **Key**: The parameter name
- **Value**: The value for this parameter

### Run Options

The Run Options tab allows you to determine how and when the strategy is triggered. The available options are as follows:

- **Run-as user**:The account used to make changes when the strategy is triggered.
- **Request batch size:** The number of records that can be included in a batch.
- **On-Demand synchronous execution:**Select to enable On-Demand synchronous execution.
- **Synchronous execution record limit:** The number of records that can be included in a synchronous execution.
- **On-Demand asynchronous execution:**Select to enable On-Demand asynchronous execution.
- **Triggers when records are added:** Causes the strategy to run any time records are added to the entity.
- **Added records filter:** Allows you to create an expression that limits the above option to run only when the records added meet certain criteria.
- **Trigger when records are updated:**Causes the strategy to run any time records in the entity are updated.
- **Updated records filter:**Allows you to create an expression that limits the above option to run only when the records edited meet certain criteria.
- **Trigger when records are deleted:**Causes the strategy to run any time records in the entity are deleted.
- **Delete records filter:**Allows you to create an expression that limits the above option to run only when the records deleted meet certain criteria.

### Scheduling

If you want to execute the strategy on a schedule, create a schedule by adding a name, Cron expression, and expression to the options under the Scheduling tab. If left blank, it will run continuously or when manually processed, depending on the run options configured.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iaf371049ffabf14.png)