# Integration Strategies

Once you have created a Service Configuration, you can create a **Strategy** to define how Profisee should interact with the configured resource. The Strategy determines how and when the service operates, and how specific actions are triggered. As part of this process, you can [create detailed expressions](https://support.profisee.com/wikis/profiseeplatform/using_the_expression_editor_in_portal) to automatically perform specified actions when a strategy is added, updated, or deleted.

## Create a Strategy

To create a Strategy:

1. Navigate to the **Strategies** window under the **Connect** tab.
2. Click the **+** icon to add a new strategy.
3. Provide a name for your strategy under the **Strategy Name** field.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ica0b3c3ee0c751ad.png)
4. Select a **Service Configuration** and **Entity** from their respective dropdown menus. You can also create a new entity by clicking the **Add new** selection. See the section below on Creating New Entities.
5. Click **Continue**. The Strategy editor is created on the page. If you do not wish to continue editing this strategy, click **Save** or **Save and** **Close**.

## Edit a Strategy

To edit a Strategy, navigate to the **Strategy** tab and select a previously configured strategy to open.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id59126fffc70d8ed.png)

When selected, the strategy opens in the strategy editor. From here, you can select between four tabs to enter/edit specific details about the strategy.

- **Overview**: Displays the general configuration details for the strategy, including the Strategy Name, Configuration, and Entity. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iba32a319758a9686.png)
- **Request**: Allows the user to map requests onto Customer Attributes. If desired, a Customer Attribute can be created as an [Expression](http://support.profisee.com/wikis/profiseeplatform/using_the_expression_editor_in_portal). The attributes are determined based on the entity and the service provider selected.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-if8e579bc613fce87.png)
- **Response Mapping**: Allows the user to map responses onto Response Properties. If desired, the Response Property can be expressed as an [Expression](http://support.profisee.com/wikis/profiseeplatform/using_the_expression_editor_in_portal). These properties may have multiple response mapping tabs based on the response code for different response types.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i90cfd6916c1cf4b0.png)
- **Run Options**: Allows the user to toggle a series of options related to On-Demand execution and Subscriptions. Includes:
- Select a run-as user.
- Allow synchronous execution
- Allow asynchronous execution
- Trigger when records are added
- Trigger when records are updated
- Trigger when records are deleted
- Delete Records from target

You can select any number of these options, but at least one must be selected.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i1e38889a75f79038.png)

Ensure that the run-as user specified is not a user that will make changes that trigger the strategy. Otherwise, the strategy will not trigger to avoid an endless loop of changes.

Note that changes made to a record by the run-as user will **not** trigger a continuous strategy associated with that record to run. It is recommended to set the run-as user to an account that does not otherwise make changes to Profisee records.

## Running or Exporting a Strategy

Once your strategy has been configured, you can manually run or export the strategy by clicking the ellipsis icon to the left of the strategy you would like to run (or right-click the strategy you would like to run) and selecting **Run** or **Export** from the dropdown menu.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i82834b7b46bc66f3.png)

### Schedules

Users can add one or more named schedules. A unique name for each schedule is provided by default, but this value can be updated if needed. A new schedule must be added as a [Cron expression](https://cronevery.day/).

## Creating New Entities through Integration Strategies

While configuring your Integration Strategy, you can create new entities via the configuration window.

1. Add or Edit an integration strategy.
2. Select the **Entity** dropdown.
3. Click *Add New...* The **Create Entity** field appears.
4. Enter a Name for the new entity.
5. Optionally enter a Description and an Icon (from FontAwesome) to be displayed with the entity.
6. Optionally, select the **Create Code values automatically** option to automatically create code values for records in this entity.
7. Optionally, include a File Attachment by clicking the + icon under **File Attachments**and including the Type and Allowed File extensions. For more information, see [File Attachments](https://support.profisee.com/wikis/profiseeplatform/add_a_file_attachment).
8. Optionally, select a Data Product to include this entity within. For more information, see [Data Products](https://support.profisee.com/wikis/profiseeplatform/Data_Products_Overview).
9. Click **Create** to finalize and create the entity. The Data Browser opens to the new blank entity.
![](https://profisee.magentrixcloud.com/sys/staticasset/read/file-i23a464be731c50e8.png)