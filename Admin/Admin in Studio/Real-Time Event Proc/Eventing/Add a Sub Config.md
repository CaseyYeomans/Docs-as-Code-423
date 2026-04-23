# Add a Subscriber Configuration

The Subscriber Configuration tab provides an interface for entering subscriber settings so that subscribers and any associated connectors can function.

You cannot save a subscriber configuration if your cluster license does not include the required connectors.

To create a subscriber configuration for the **Data Service Controller**:

- The configuration options on this tab are dependent on the selected subscriber. Select each field, and detailed information on completing the field appears under the configuration grid. If an Integrator strategy file is required, it must be created using Profisee (R) Integrator (formerly Federation Manager).
- If a strategy is included in the configuration, the Profisee service user must have access to the file location where the strategy is located.
- If the Profisee connection in the Integrator strategy differs from the current server, then the current server will be used as the connection instead. For more information, see [Overriding connections in Integrator strategies](https://support.profisee.com/wikis/profiseeplatform/override_connections_in_integrator_strategies).

1. In the navigation panel, click **Real-Time Event Processing**, under Administration.
2. On the Real-Time Event Processing tab, click **Subscriber configurations**.

The Subscriber Configurations tab displays.
3. On the toolbar, click **New**.
4. On the Name and Context tab, in the Configuration Name field, enter a name for the subscriber configuration.
5. Select the subscriber to use from the **Subscriber** list.

The registered subscribers display in this list. If the list is blank, select Register New Subscriber to complete the registration process.

6. Select the source system type from the **Source System Type** list.

The options available in the Source System Type list will vary, depending on the type of subscriber selected.

7. On the Properties tab, complete the configuration for the selected subscriber.

The two most common subscribers are the Data Transfer Controller and the Data Service Controller, and detailed instructions for configuring these follow.

To create a subscriber configuration for the **Data Transfer Controller**:

1. In the **Strategy File** or **Strategy File Path** fields, browse to, or type the file path, to the data transfer strategy file created using Integrator. Data transfer strategies have the \*.mfed extension.
2. From the **Transfer Action** list, select the transfer action to use in this subscription. Note that the action you select must be included in the selected strategy file.
3. In the **Creation Wait Time** field, enter a value (in seconds) to wait before Profisee requests the members.

The Creation Wait Time is in seconds, and it makes sure the external system fully commits a Create action before Profisee requests the member. On some systems, new members are not committed until the entire update process successfully completes. This may take a few seconds to occur, and if Profisee makes a request for the new members during that time, then the system will return an error.

The suggested value is 15 seconds. You may need to adjust this value depending on the speed of your server hardware, potential network latency, and other factors that can affect how quickly new members are created.
4. In the **Strategy File** or **Strategy File Path** fields, browse to, or type the file path, to the data service strategy file created using Integrator. Data service strategies have the \*.fmdss extension.
8. After an Integrator strategy is associated with the subscriber, you can click Write to File to save the strategy as an XML file.

This step is optional but useful for troubleshooting purposes.
9. Click **Save** or **Save and close** when you have completed configuring the subscriber.

After completing the subscriber configuration, the next step is to define triggering actions and the associated subscriptions.