# Customize Context Buttons

The Forms Designer context buttons allow you to define actions that occur prior to or following four basic types of tasks:

- Approving or rejecting
- Contributing to a task
- Adding a new member through the Profisee Portal
- Editing a member through the Profisee Portal

The custom context buttons are included in form where they are configured.

You can configure pre-actions and post actions:

- **Pre-Action**: When the user clicks the button, the pre-action runs first, and then the button action is processed.
- **Post-Action**: When the user clicks the button, the action associated with the button runs first. Then, the post-action runs.

For more information on the specific script actions you can use with buttons, see [Configuring form script actions](https://support.profisee.com/wikis/profiseeplatform/using_form_script_actions).

Pre- and post-actions can perform tasks like refreshing a control after a member is saved, showing a confirmation dialog after a user clicks Approve, or triggering an event in Profisee event processing.

To customize a context button:

1. [Edit](https://support.profisee.com/wikis/profiseeplatform/edit_form) an existing form, or [create a new form](https://support.profisee.com/wikis/profiseeplatform/create_a_new_form).
2. In the edit panel toolbar, click **Properties**.

The Form Properties dialog appears.
3. Click the **Context Buttons** tab.
4. Click the button you want to customize.

For more information on the buttons and how they are used, see [Using context buttons.](https://support.profisee.com/wikis/profiseeplatform/use_context_buttons)
5. To define a pre-action for the selected button:

1. In the Context Button Actions dialog, click the **Pre-Actions** menu.
2. Select the script action that you want to process before the button action processes.
3. Click **Add**.
4. Configure the script action, if necessary, using the properties displayed in the Action Properties panel.
5. Repeat to add additional pre-action scripts.
6. To define a post-action for the selected button:

1. In the Context Button Actions dialog, click the **Post-Actions** menu.
2. Select the script action that you want to process before the button action processes.
3. Click **Add**.
4. Configure the script action, if necessary, using the properties displayed in the Action Properties panel.
5. Repeat to add additional post-action scripts.
7. Click **Save**.