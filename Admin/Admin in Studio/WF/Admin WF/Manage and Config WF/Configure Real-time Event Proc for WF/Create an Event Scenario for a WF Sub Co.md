# Create an Event Scenario for a Workflow Subscriber Configuration

After you have created a subscriber configuration for the Workflow subscriber, you can create an **event scenario** that uses the subscriber configuration.

**IMPORTANT**: When using a workflow in event processing, do not use events resulting from a workflow as triggers for the same workflow. The workflow will be initiated over and over in an endless cycle.

External events cannot directly initiate workflows. Only Profisee events can initiate workflows in event processing. However, an external event may result in a data change that triggers initiation of a workflow.

1. In the navigation panel, click **Real-Time Event Processing**, under Administration.
2. On the Real-Time Event Processing tab, click **Profisee event scenarios and subscriptions**.

The Profisee Events Scenario tab displays.
3. Click **New** in the toolbar.
4. Complete the information for the triggering event on the Name and Context tab, under Triggering Rules:

- **Name**: The name of the event.
- **Entity**: The entity containing the attributes that will trigger the event.
- **Triggering Actions** : Define the actions in the triggering event.

- **Create**: Creating a new member is the triggering action.
- **Update**: Changing a member is the triggering action.
- **Delete**: Deleting a member is the triggering action.
- **On demand**: Users can click a menu item that equates to performing data changes matching the scenario. No data is changed, but the event consuming server passes a notification event to the subscriber, indicating that a scenario has occurred, and that the linked configuration should launch.
- Enabled: Toggling this options lets you enable or disable the event scenario.

When the event scenario is disabled and event processing is paused, the subscriber will continue processing queued events when the event scenario is enabled again and event processing resumes.

5. If the selected triggering action is an update action, make your selections on the Attributes tab.

For Create and Delete triggering actions, the Attributes tab is disabled, as attribute selection is unnecessary for those actions.

Options include:

- **All attributes**

An update to any value of any attribute in the entity is a triggering action. This includes not only the attributes that are currently in the entity, but any attributes that are added in the future.
- **Selected attributes**

An update to any value in the selected list of selected attributes is a triggering action.

Selecting all of the attributes under Selected attributes does not include any attributes added in the future.
6. Click **Edit Trigger Values** and (optionally) enter the specific attribute values to trigger events.

This option is not available when All attributes is selected.

You can now initiate a workflow based on your selections for the event scenario.