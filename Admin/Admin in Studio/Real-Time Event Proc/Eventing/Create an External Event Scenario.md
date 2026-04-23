# Create an External Event Scenario

Creating an external event scenario makes it possible to launch event processing subscriptions based on event scenarios occurring on external systems. To create an external scenario, you must first configure the external system to detect relevant events. This involves registering a Profisee plug-in on the system, plus defining the scenarios which will trigger events. For more information, refer to the Profisee (R) Integrator (formerly Federation Manager) help system.

External scenarios are, for the most part, defined on the external system. However, you must also configure the external event on Profisee to link the occurrence of the event on the external system with a Profisee subscription.

After the external system has been correctly configured to detect events, follow these steps to create an external scenario:

1. In the navigation panel, click **Real-Time Event Processing**, under Administration.
2. On the Real-Time Event Processing tab, click **External event scenarios and subscriptions**.

The External Event Scenarios tab displays.
3. Click **New** in the toolbar.
4. Complete the information for the triggering event on the Name and Context tab, under Triggering Rules:

- **Event Name**: The name of the event.

The event name must match exactly the configured event name in the tag for the event on the external system.

- **Entity Name**: The entity on the external system that will trigger the event.

This is the entity name in the external system. It should match the name of the entity you selected in the Integrator strategy. Type the entity name exactly as it appears in the external system.

- **External System**: The external system to monitor for event scenarios.

The list includes the entries in the Profisee external systems list. If this list is empty, add one or more external systems to the Profisee external systems list. For more information, see [External Systems List overview](https://support.profisee.com/wikis/profiseeplatform/external_systems_list_overview).

- **Target Model**: The Profisee model where data from the external system will transfer to. If you are using the data transfer controller, then the target model is the same as the target model included in your data transfer strategy in the subscription.
- **Triggering Actions**: Select one or more triggering actions.

While it is possible to select any combination of actions, the only selections are those configured on the external system in the event tag.

- **Create**: Creating a new member is the triggering event
- **Update**: Editing a member is the triggering event
- **Delete**: Deleting a member is the triggering event

At present, only Create and Update are supported.

- Enabled: Toggling this options lets you enable or disable the event scenario.

5. Select the attributes on the Attributes tab.

**--or--**

- **All attributes**

Any attributes in the external system scenario can trigger the event.
- **Specific attributes**

Only the selected list of selected attributes in the list can trigger the event.

You must manually type the attribute names into the Value list. Be sure to use the internal system name, not the display name, for the attribute.

6. Select the event tags on the Event Tags tab.

Event tags are configured on the external system. The method used to create them varies, depending on the external system type, and event tags can generally be anything you choose. Event tags are a way for Profisee to identify external events and map them to event processing so that they can be used to trigger different events based on the tags.

**--or--**

- **All tags**

Any tag in the external system scenario can trigger the event.
- **Specific tags**

Only the selected list of selected tags in the list can trigger the event.

You must manually type the event tags into the Value list.

7. On the Subscriptions tab, select the subscriber to use with the scenario you have just defined.

Note: If the list of available subscriber configurations is empty, there are no configured subscribers which apply to this scenario. Go back to the Subscriber configurations tab to add a subscriber configuration.
8. When the scenario is complete, click **Save** or **Save and close** to save it and close the configuration tabs.
9. Start Event Processing if it is not already running.