# Trigger Internal Event Script Action

The Trigger Internal Event script action simulates the data changes necessary to trigger event processing. This script action behaves the same way as the Trigger Internal Events option available in the Profisee FastApps Studio entity grid.

To add the Trigger Internal Event script action to a button:

1. From the list of actions, select **Trigger Internal Event**, and then click **Add**.

The properties display in the Action Properties panel.
2. Click the **Event** list, and then select the event scenario that should be simulated when the button is clicked.

The **Entity** field populates with the model and entity in the event.

While no changes to data occur when triggering an event this way, a triggering event occurs. The resulting event is processed according to the subscription settings in event processing. Triggering an event in this way is the same as triggering an event from the entity grid using the Trigger Internal Events option.

3. If necessary, enter a code in the **Member Code** field to indicate the member responsible for triggering the event. If no member code is specified, then the code of the member in the form will be used.
4. Click **OK**.

The event scenario must have the **On demand** option selected in order for the event scenario to appear in the list. For more information, see [Configuring data transfers with Profisee as the source server](https://support.profisee.com/wikis/profiseeplatform/configure_data_transfers_with_profisee_as_the_source_server).

## See Also

[Customize Context Buttons](https://support.profisee.com/wikis/profiseeplatform/customize_context_buttons)

[Add a Script Action to a Button in a Form Layout](https://support.profisee.com/wikis/profiseeplatform/add_script_action_form_button)