# Create an Internal Event Scenario

Creating an internal event scenario is the final step to configuring real-time event processing. To create a scenario, you must first register a subscriber and create a configuration for the subscriber. For some subscribers, like the Data Transfer Controller and the Data Service Controller, you will also need to create a data transfer or data service strategy. For more information on strategies, refer to the help system in Profisee (R) Integrator (formerly Federation Manager).

Internal event scenarios can only be created using subscriber configurations where the source system type is Profisee.

To create a Profisee scenario:

1. In the navigation panel, click **Real-Time Event Processing**, under Administration.
2. On the Real-Time Event Processing tab, click **Internal event scenarios and subscriptions**.

The Internal Events Scenario tab displays.
3. Click **New** in the toolbar.
4. Complete the information for the triggering event on the Name and Context tab, under Triggering Rules:

- **Name**: The name of the event.
- **Entity**: The entity containing the attributes that will trigger the event.
- **Triggering Actions**: Define the actions in the triggering event.

- **Create**: Creating a new member is the triggering action.
- **Update**: Changing a member is the triggering action.
- **Delete**: Deleting a member is the triggering action.
- **On demand**: Users can click a menu item that serves as the equivalent of performing data changes matching the scenario. No data is changed, but the event consuming server passes a notification event to the subscriber, indicating that a scenario has occurred, and that the linked configuration should launch.
- **Enabled**: Toggling this options lets you enable or disable the event scenario.

When an event scenario is disabled and event processing is paused, the subscriber will continue processing queued events when the event scenario is enabled again and event processing resumes.

5. If the selected triggering action is an update action, make your selections on the Attributes tab.

For Create and Delete triggering actions, the Attributes tab is disabled, as attribute selection is unnecessary for those actions.

Options include:

**--or--**

- All Attributes

An update to any value of any attribute in the entity is a triggering action. This includes not only the attributes that are currently in the entity, but any attributes that are added in the future.
- Selected attributes

An update to any value in the selected list of selected attributes is a triggering action.

If you want Eventing to trigger when values are null, select the **Include Blanks** checkbox and add specified values. If you want eventing to trigger *only* when values are null, select the Include Blanks checkbox and include no attribute values.

Selecting all of the attributes under Selected attributes does not include any attributes added in the future.

6. Click Edit Trigger Values and (optionally) enter the specific attribute values to trigger events.

This option is not available when All attributes is selected.

7. On the Subscriptions tab, select the subscriber to use with the scenario you have just defined.

If the list of available subscriber configurations is empty, there are no configured subscribers which are applicable for this scenario. Go back to the Subscriber configurations tab to add a subscriber configuration.

The subscriber configuration is called a subscription after it is linked to a scenario.
8. When the scenario is complete, click **Save** or **Save and close** to save it and close the configuration tabs.