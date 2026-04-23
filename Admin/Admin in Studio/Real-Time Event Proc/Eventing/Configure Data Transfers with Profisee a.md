# Configure Data Transfers with Profisee  as the Source Server

With Profisee as the source, you can use subscribers to perform data transfers from Profisee to an application server supported by Profisee connectors. For a comprehensive list of available connectors, see [https://www.profisee.com](http://www.profisee.com/).

Keep in mind that data transfers using event processing occur comparatively slowly. Profisee must perform a publish action for each member that is added or updated. For this reason, the best use of event processing is to keep systems synchronized when changes occur. To perform large volume initial data loading, use the command line Integrator CLU (formerly FederationTransfer) option in Integrator (formerly Federation Manager) instead.

## Prerequisites

To trigger data transfers from Profisee to another system, you must have:

- Servers in the same Profisee cluster with the following roles:
- Event consuming
- Event publishing
- Web application
- The Data Transfer Controller subscriber, installed on an event consuming server
- The Profisee DataTransfer connector installed on the event consuming server

A data transfer strategy, created on Profisee (R) Integrator containing connection information for the source Profisee server and the target system, as well as attribute mappings between attributes on the source and target systems

All three server roles (event consuming, event publishing, Web application) can be assigned to the same server. The Profisee source system must be located in this cluster.

This strategy provides a link between the source entity and attributes and the target entity and attributes. It also provides security, making sure that only the user with credentials stored in the strategy file is able to transfer data to the target system. For more information on how to create a data transfer strategy, refer to the documentation in Integrator.

## Procedure

To configure data transfers from Profisee to another system, perform the following configuration steps on the source server. See the Related Topics section for greater detail on each step.

Note: If the source Profisee connection in the data transfer strategy differs from the current server, then the current server will be used as the connection instead. For more information, see [Overriding Connections in Integrator Strategies](https://support.profisee.com/wikis/profiseeplatform/override_connections_in_integrator_strategies).

1. Register the Data Transfer Controller subscriber.

1. On the Subscribers tab, locate the Data Transfer Controller subscriber in the list of Available Subscribers.
2. Select the subscriber, and then click the right arrow to add it to the Registered Subscribers list.
3. Click **Save and Close**.
2. Configure the subscriber.

If you choose the **Publish to Profisee** option from Integrator when creating a data transfer strategy, Integrator will create the subscriber configuration for you, and you can skip this step. All possible transfer actions are included when using this method, so be sure to check this section to make sure the selection meets your needs.

1. On the Subscriber Configurations tab, click **New**.
2. In the Configuration Name field, enter a name for the configuration.
3. Select the Data Transfer Controller from the Subscriber list.
4. Select **Profisee** from the Source System Type list.
5. Click the **Properties** tab.
6. Click inside the Strategy File field, browse to the data transfer strategy, and select it.
7. Select the **Transfer Action** from the list.

These selections define the actions that occur when the event is triggered. Options include:

You must select one transfer action for the configuration, and the selected transfer action must be included in the selected data transfer strategy. For example, if the strategy includes all three transfer types, you can select any transfer action. However, if the only transfer action in the strategy is Insert, then you will only be able to select Insert for the transfer type in the subscriber configuration.

- **Insert**

New members are created on the target (edited members are not updated)
- **Update**

Existing members are updated on the target (new members are not created)
- **Upsert**

Create new members and update existing members on the target

1. Click **Save**.

The subscriber properties validate.
2. Fix any configuration validation issues, and then click **Save and Close**.

3. Create the scenario and link the subscriber configuration to it.

1. On the Profisee Event Scenarios tab, click **New**.
2. On the Name and Context tab, in the **Name** field, enter a name for the scenario.
3. From the **Entity** list, select the entity that will trigger events.
4. Under **Triggering actions**, select the actions within the entity that can trigger events.

- **Create**

When a new member is created, the event is triggered.
- **Update**

When an existing member is edited, the event is triggered.

Creating a new member can also produce Update events. When a new member is published, it is reported as a Create action when the member contains a Code value and no other attribute values. When a new member contains values for Code and any other attributes, Profisee reports a Create action for the Code and Update actions for all other attributes.
- Delete

**When** an existing member is deleted, the event is triggered.
- **On demand**

Selecting this option allows users to cause a triggering action to occur without making any data changes. This option is accessed using the **Trigger Profisee Events** right-click menu option in the entity grid.
5. Select **Enabled** to enable this scenario.

The scenario is not active until the scenario is saved with the Enabled option selected.
6. If you have selected **Update** as a triggering action, select the **Attributes** tab to select the attributes, and select the attributes that will trigger the event.
7. Select the **Subscriptions** tab and select the subscriber configuration to use with this scenario.
8. When you have finished configuring all four tabs, click **Save and close**.
4. Start Event Processing if it is not already running.

The Profisee data transfer is ready to use. To test it, perform the triggering action, or use the entity grid menu option to trigger it manually (if On Demand is included as a triggering action in the scenario).