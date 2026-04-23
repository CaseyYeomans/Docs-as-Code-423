# Initiate Workflow Script Action

The Initiate Workflow script action causes a workflow to begin when the user clicks the button in the form.

To add the Initiate Workflow script action to a button:

1. From the list of actions, select **Initiate Workflow**, and then click **Add**.

The properties display in the Action Properties panel.

The only property that is required is the Workflow ID property. This property contains the URI of the workflow.

2. Click the **Workflow ID** list, and then select the Workflow to use.

The following properties are populated automatically:

- Workflow URI
- Entity
3. Complete member code information, if necessary.

If not specified, the member code defaults to the initiating member.
4. Click **OK**.

The workflow initiated by the script must be properly registered and configured before the Initiate Workflow action can be added to a form.

When a workflow is initiated by another workflow, the user is the application pool assigned to that workflow. Since this user is not a Profisee user, no user information displays in Analytics reports that include initiating user information.

## See Also

[Customize Context Buttons](https://support.profisee.com/wikis/profiseeplatform/customize_context_buttons)

[Add a Script Action to a Button in a Form Layout](https://support.profisee.com/wikis/profiseeplatform/add_script_action_form_button)