# Using the D&B Hierarchies & Connections Service Provider

Profisee Administrators can use the **D&B Hierarchies & Connections** Service Provider to identify entities associated with a given company in terms of legal ownership, franchises, and other connection types.

# Adding a New D&B Hierarchies & Connections Service Configuration

When adding a new service configuration for this service provider, you must configure it with the following settings:

- **Service**: The Data Blocks Level to be used for this configuration. This service defaults to Level 1 for this service provider.
- **Data Blocks Level 1**: Basic information about a company primarily used to validate the Match found in Company Entity Resolution such as Business Name, Primary Address, Telephone, Web Address and Primary Industry Codes.
- **Configuration Name**: The user-defined name for this configuration.

When finished, click **Continue** to create the service configuration.

## D&B Hierarchies & Connections Configuration

Once created, you may view/edit the following options on the **Overview** and **Settings**tabs.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i1533ef8c43013881.png)

### Overview

The Overview section allows you to view the configuration name, service provider, provider type, and service previously configured. Of these, only the configuration name can be edited.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iaf9a0b2b8a74a480.png)

### Settings

#### Authentication

- **OAuth Url**: The URL for your OAuth credentials.
- **Client ID**: The Client ID for your OAuth account.
- **Client Secret**: The secret for your OAuth account.
- **OAuthScope**: The specific level of access for your OAuth account.

#### Service Parameters

- **Block Id**: The ID defining the Data Blocks level previously configured. This setting cannot be edited.

# Creating a new Strategy using the D&B Hierarchies & Connections Service Configuration

## Adding a New D&B Hierarchies & Connections Strategy

When adding a new integration strategy using a D&B Hierarchies & Connections-based Server Configuration, the strategy gains no new options beyond the standard Integration Strategy Options.

1. Navigate to the **Strategies** window under the **Connect** tab.
2. Click the **+** icon to add a new strategy.
3. Provide a name for your strategy under the **Strategy Name** field.
4. Select the service configuration created previously from the **Service Configuration** dropdown.
5. Select an Entity from the **Entity** dropdown menu, or create a new entity by clicking the **+** icon.
6. Click **Continue**. The Strategy editor is created on the page. If you do not wish to continue editing this strategy, click **Save** or **Save and** **Close**.

## Configuring the Strategy

Once the Strategy is created, complete the settings on the following tabs. When finished configuration on any tab, click **Save** or **Save and Close** to confirm your changes.

### Overview

The Overview tab allows you to view the previously configured Strategy Name, Configuration, and Entity. Of these, only the Strategy Name can be edited.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic9ae2da89f771ea9.png)

### Request

#### Mapping Customer to Request

This tab allows you to map Request Properties onto Customer Attributes, or use the Aisey-powered Assign button to automatically suggest mappings. You can also manually create expressions using the [expression editor](https://support.profisee.com/wikis/profiseeplatform/using_the_expression_editor_in_portal) to define a customer attribute with specific parameters.

The DUNS Number required as the first property can be located by using the D&B Identity Resolution service provider.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3a4ce4c2a7837dc4.png)

### Response

#### Mapping Default Response to Customer

This tab allows you to map Customer Attributes onto Response Properties with their associated types, or use the Aisey-powered Assign button to automatically suggest mappings. You can also manually create expressions using the [expression editor](https://support.profisee.com/wikis/profiseeplatform/using_the_expression_editor_in_portal) to define a response property with specific parameters.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i379be076b99e85a8.png)

#### Run Options

The Run Options tab allows you to determine how and when the strategy is triggered. The available options are as follows:

- **Run-as user**:The account used to make changes when the strategy is triggered.
- **On-Demand synchronous execution:** Select to enable On-Demand synchronous execution.
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