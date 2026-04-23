# Using the D&B Identity Resolution Service Provider

Profisee Administrators can use the **D&B Identity Resolution** Service Provider to append a company's DUNS (Data Universal Numbering System) number. This allows you to submit information about a company to return a DUNS number, which can be used to retrieve additional information about that company.

# Adding a New D&B Identity Resolution Service Configuration

When adding a new service configuration for this service provider, you must configure it with the following settings:

- **Service**: The Identity Resolution service to be used for this configuration. Currently, the only available option is Identity Resolution Cleanse Match, and it is selected by default.
- **Configuration Name**: The user-defined name for this configuration.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i280de583ba159b2.png)

When finished, click Confirm to create the service configuration.

## D&B Identity Resolution Configuration

Once created, you may view/edit the following options on the **Overview**tab.

### Overview

The Overview section allows you to view the configuration name, service provider, provider type, and service previously configured. Of these, only the configuration name can be edited.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3ac0e853a59a6240.png)

# Creating a new Strategy using the D&B Identity Resolution Service Configuration

## Adding a New D&B Identity Resolution Strategy

When adding a new integration strategy using a D&B Identity Resolution-based Server Configuration, the strategy gains no new options beyond the standard Integration Strategy Options.

1. Navigate to the **Strategies** window under the **Connect** tab.
2. Click the **+** icon to add a new strategy.
3. Provide a name for your strategy under the **Strategy Name** field.
4. Select the Webhook-based service configuration created previously from the **Service Configuration** dropdown.
5. Select an Entity from the **Entity** dropdown menu, or create a new entity by clicking the **+** icon.
6. Click **Continue**. The Strategy editor is created on the page. If you do not wish to continue editing this strategy, click **Save** or **Save and** **Close**.

## Configuring the Strategy

Once the Strategy is created, complete the settings on the following tabs. When finished configuration on any tab, click **Save** or **Save and Close** to confirm your changes.

### Overview

The Overview tab allows you to view the previously configured Strategy Name, Configuration, and Entity. Of these, only the Strategy Name can be edited.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i8987301e14ccb4e3.png)

### Request

#### Mapping Customer to Request

This tab allows you to map Request Properties onto Customer Attributes, or use the Aisey-powered Assign button to automatically suggest mappings. You can also manually create expressions using the [expression editor](https://support.profisee.com/wikis/profiseeplatform/using_the_expression_editor_in_portal) to define a customer attribute with specific parameters.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i7b8a62f12f74d670.png)

### Response

#### Mapping Default Response to Customer

This tab allows you to map Customer Attributes onto Response Properties with their associated types, or use the Aisey-powered Assign button to automatically suggest mappings. You can also manually create expressions using the [expression editor](https://support.profisee.com/wikis/profiseeplatform/using_the_expression_editor_in_portal) to define a response property with specific parameters.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id5eaf34900552ac7.png)

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