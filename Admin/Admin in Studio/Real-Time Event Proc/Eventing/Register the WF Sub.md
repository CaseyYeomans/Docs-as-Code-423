# Register the Workflow Subscriber

The Profisee workflow subscriber initiates workflows based on created, updated, or deleted data in the various model entities. Before you can trigger workflows based on the data changes, you must first register the workflow subscriber. The workflow subscriber is installed when the Profisee server is installed on a node in your cluster.

To register the Workflow subscriber in Profisee :

1. In the navigation panel, click **Real-Time Event Processing**, under Administration.
2. On the Real-Time Event Processing tab, click **Subscribers**.

The Subscriber registration tab displays.
3. Select the Workflow subscriber in the **Available Subscribers** pane.

The subscribers listed in this panel are the subscribers installed on all event consuming servers in the cluster.

If the Workflow subscriber does not appear in the list, make sure it is installed properly. For more information, see [Installing subscribers on the event consuming server](https://support.profisee.com/wikis/profiseeplatform/install_subscribers).

5. Click the right arrow to add the subscriber to the Registered Subscribers column.
6. Click **Save** or **Save and Close** to save the registered subscriber.

As with other types of subscribers, the next step is to create a [subscriber configuration](https://support.profisee.com/wikis/profiseeplatform/create_a_configuration_for_the_workflow_subscriber) after registering it.