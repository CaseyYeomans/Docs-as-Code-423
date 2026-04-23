# Create a Configuration for the Workflow Subscriber

The Subscriber Configuration tab provides an interface for entering subscriber settings so that subscribers and any associated connectors can function.

You cannot save a subscriber configuration if your cluster license does not include the required connectors.

To create a subscriber configuration:

1. In the navigation panel, click **Real-Time Event Processing**, under Administration.
2. On the Real-Time Event Processing tab, click **Subscriber configurations**.

The Subscriber Configurations tab displays.
3. On the toolbar, click **New**.
4. On the Name and Context tab, in the Configuration Name field, enter a name for the subscriber configuration.
5. Select the Workflow subscriber from the **Subscriber** list.

The registered subscribers display in this list. If the subscriber is not listed, select Register New Subscriber to go back to the Subscribers tab and register the Workflow subscriber.

6. Select the source system type from the **Source System Type** list.

The Source System Type field automatically displays Profisee as read-only.

7. On the Properties tab, complete the configuration for the selected subscriber.

1. In the Map section, in the **Workflow URI** field, paste the path to workflow URI.

Use the following format, based on the path to your workflow \*.xamlx file in IIS:

net.tcp://myServer.myDomain.com/siteName/workflowName.xamlx
2. In the Errors section, choose how to handle communications exceptions.

If you want the workflow to continue trying to communicate when there is a communication failure, clear the selection.

If you want the workflow to stop when there is a communication failure, leave the option selected.
8. Click **Validate Properties** to test the subscriber configuration.
9. If there are no errors for the configuration, click **Save and Close**.

You are now ready to create an event scenario.

## See Also

[Create an External Event Scenario](https://support.profisee.com/wikis/profiseeplatform/create_an_external_event_scenario)

[Create an Internal Event Scenario](https://support.profisee.com/wikis/profiseeplatform/create_an_internal_event_scenario)