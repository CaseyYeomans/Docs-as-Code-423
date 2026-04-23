# Configure External Data Transfers with Profisee as the Target Server

In addition to supporting data transfers with Profisee as the data source, event processing also supports transfers from external systems with Profisee as the target to receive data.

Profisee currently supports data transfers between Profisee and several types of application servers, using specific connectors designed to connect to those systems. For a comprehensive list of available connectors, visit Profisee.com at <http://www.profisee.com>.

This procedure applies only to transfers to Profisee where the source server is not also a Profisee server. For transfers where Profisee is the source, refer to [Configuring Data Transfers with Profisee as the Source Server](https://support.profisee.com/wikis/profiseeplatform/configure_data_transfers_with_profisee_as_the_source_server) and [Special Considerations for Profisee-to-Profisee Data Transfers](https://support.profisee.com/wikis/profiseeplatform/special_considerations_for_profisee_to_profisee_data_transfers) for more information.

Keep in mind that data transfers using event processing occur comparatively slowly. Profisee must perform a publish action for each member that is added or updated. For this reason, the best use of event processing is to keep systems synchronized when changes occur. To perform large volume initial data loading, use the command line Integrator CLU (formerly FederationTransfer) option in Integrator (formerly Federation Manager) instead.

## Prerequisites

To trigger data transfers between Profisee and an external system, you must have, at minimum, a cluster containing the following:

- A valid account and credentials for the external system

For specific external system requirements, refer to the Profisee (R) Integrator documentation.

- A custom plug-in running on the external system that passes events from the system to Profisee
- An entry in your Profisee External Systems List for the external system
- Servers in the same Profisee cluster with the following roles:

- Event consuming
- Background Task Processor
- Web application

All three server roles (event consuming, event publishing, Web application) can be assigned to the same server.

- The Data Transfer Controller subscriber, installed on an event consuming server
- The Profisee DataTransfer connector installed on the event consuming server
- A data transfer strategy, created using Profisee (R) Integrator, with Profisee as the target server and the external system as the source

This strategy provides a link between the Profisee model, entity and attributes to the external system entity. It also provides security, making sure that only the user with credentials stored in the strategy file is able to transfer data to the target system. For more information on how to create a data transfer strategy, refer to the Integrator help system.

## Procedure

Perform the following steps on the Profisee server with the Web application role in the cluster:

1. Register the Data Transfer Controller subscriber.

1. From the Real-Time Event Processing tab under administration, click Subscribers.
2. On the Subscribers tab, locate the Data Transfer Controller subscriber in the list of Available Subscribers.
3. Select the subscriber, and then click to add it to the Registered Subscribers list.
4. Click **Save and Close**.

If the Profisee connection in the data transfer strategy differs from the current server, then the current server will be used as the connection instead. For more information, see [Overriding connections in Integrator strategies](https://support.profisee.com/wikis/profiseeplatform/override_connections_in_integrator_strategies).

2. Configure the subscriber.

If you choose the **Publish to Profisee** option from Integrator when creating a data transfer strategy, Integrator will create the subscriber configuration for you, and you can skip this step.

1. From the Real-Time Event Processing tab under administration, click **Subscriber configurations**.
2. On the Subscriber Configurations tab, click **New**.
3. In the Configuration Name field, enter a name for the configuration.
4. Select the Data Transfer Controller subscriber from the **Subscriber** list.
5. From the **Source System Type** list, select the external system.
6. Click the **Properties** tab.
7. Click inside the Strategy File field, browse to the data transfer strategy, and select it.
8. Select the **Transfer Action** from the list.

These selections define the actions that occur when the event is triggered. Options include:

You must select one transfer action for the configuration, and the selected transfer action must be included in the selected data transfer strategy. For example, if the strategy includes all three transfer types, you can select any transfer action. However, if the only transfer action in the strategy is Insert, then you will only be able to select Insert for the transfer type in the subscriber configuration.

- **Insert**

New members are created on the target (edited members are not updated)
- **Update**

Existing members are updated on the target (new members are not created)
- **Upsert**

Create new members and update existing members on the target

9. Click **Validate Properties**.
10. When there are no errors, click **Save and Close**.

2. Define the external event that triggers and link the subscriber configuration to it.

1. From the Real-Time Event Processing tab under administration, click **External event scenarios and subscriptions**.
2. On the External Event Scenarios tab, click **New**.
3. On the Name and Context tab, in the **Event Name** field, enter a name for the triggering external event. The event name must match exactly the configured event name in the tag for the event on the external system.
4. In the **Entity Name** field, type the name of the entity that will trigger the event. This is the entity name in the external system. It should match the name of the entity you selected in the data transfer strategy. Type the entity name exactly as it appears in the external system.
5. From the **External System** list, select the external system configured in Profisee that will trigger the event. The entries in the external systems list are included in this list, configured on the External Systems List tab. If this list is empty, go to the External Systems List tab and configure the external system.
6. Under **Triggering actions**, select the actions within the entity that will trigger the event. While it is possible to select any combination of actions, the only selections are those configured on the external system in the event tag.

- **Create**: Creating a new member is the triggering event
- **Update**: Editing a member is the triggering event
- **Delete**: Deleting a member is the triggering event

**NOTE**: At present, only Create and Update are supported.
7. Select **Enabled** to enable this scenario. The scenario is not active until the scenario is saved with the Enabled option selected.
8. Select the attributes on the Attributes tab.

**--or--**

- **All attributes**

Any attributes in the external system scenario can trigger the event.
- **Specific attributes**

Only the selected list of selected attributes in the list can trigger the event. You must manually type the attribute names into the Value list. Be sure to use the internal system name, not the display name, for the attribute.
9. Select the event tags on the Event Tags tab.

Event tags are configured on the external system. The method used to create them varies, depending on the external system type, and event tags can generally be anything you choose. Event tags are a way for Profisee to identify external events and map them to event processing so that they can be used to trigger different events based on the tags.

**--or--**

- **All tags**

Any tag in the external system scenario can trigger the event.
- **Specific tags**

Only the selected list of selected tags in the list can trigger the event. You must manually type the event tags into the Value list.
10. Select the **Subscriptions** tab and select the subscriber configuration to use with this scenario. The subscriber configuration is called a subscription after it is linked to a scenario.
11. When you have finished configuring the settings, click **Save and close**.
3. Start Event Processing if it is not already running.