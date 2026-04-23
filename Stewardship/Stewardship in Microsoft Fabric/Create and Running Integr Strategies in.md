# Creating and Running Integration Strategies in Fabric

You can use integration strategies to connect a Profisee and OneLake database and exchange data between the two databases. Integration strategies determine how and when the service operates and how specific actions are triggered.

To create a new integration strategy:

1. Click the **Add an Integration Strategy** button on the Home tab. The **Create Integration Strategy** page opens.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i89c75f4636d8ab6a.png)
2. Select an existing service configuration from the **Service Configuration** dropdown, or select **Create new** to create a new service configuration.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ia3705243710e9039.png)
1. If creating a new service configuration, enter the information on the following fields:
- **Name**: The Unique Name for the configuration.
- **Client ID**: The Client ID credentials for the associated authenticator.
- **Secret**: The secret credentials for the associated authenticator.
- **Database**: The OneLake database to import or export data from. This list is populated based on the client credentials specified above.
3. Click **Next**.
4. Select the following for your Integration Strategy:![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i19fd9810d477faa4.png)
- **Entity**:Select an entity from the dropdown selector to be used in the integration strategy, or create a new entity to be used.
- **OneLake Dataset**:Select the OneLake dataset to use from the dropdown selector.
- **Integration Flow**: The Integration Flow allows you to Import (From OneLake into Profisee) or Export (Profisee into OneLake) your view. If you want to perform both flows, you must create an additional strategy.
5. Click **Finish**.

The Integration Strategy is now created and can be configured and run. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i7f1d24d1122b9829.png)

The header displays the Strategy Name, Entity, OneLake Dataset, Integration Flow, and Run as User as configured previously. The Strategy Name and Run-as User can be edited before running the strategy. You can also check the checkbox for **On-Demand asynchronous execution.** It is recommended to check this option before running the strategy in most cases to prevent issues.

Under **Customer Mapping**, you can map Profisee attributes onto OneLake Customer Attributes, which must be completed before the strategy can run. If desired, a Customer Attribute can be created as an [Expression](http://support.profisee.com/wikis/profiseeplatform/using_the_expression_editor_in_portal) to add specific parameters around it. For example, you could add an expression to map a customer attribute onto multiple Profisee attributes (or vice versa). You can also add a new attribute by clicking the **Add attribute** button at the bottom of the Customer Mapping area.

When you are finished making changes, you can click **Save** or **Save and Close** to save your changes. When you are ready to run the integration strategy, navigate to the Run tab on the top-left of the Integration Strategy Configuration pane, then click **Run**. You can also click **View Run History** to view a log of previous times the strategy was run and which user ran it.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i38e9f708c34e850a.png)