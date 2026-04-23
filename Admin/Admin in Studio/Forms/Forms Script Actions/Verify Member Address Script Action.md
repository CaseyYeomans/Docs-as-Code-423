# Verify Member Address Script Action

The Verify Member Address script action processes a verification strategy for the configured member (or for the member indicated by the form when no member code is configured) when the user clicks the button.

To add the Verify Member Address script action to a button:

1. From the list of actions, select **Verify Member Address**, and then click **Add**.

The properties display in the Action Properties panel.
2. In the Action Properties panel, click the **Address Strategy** list, and then select the verification strategy to run when the button is clicked.

**NOTE**: Only the verification strategies applicable to the form and workflow context display in the list.
3. Click inside the **External Service Types** row, and then click the ellipsis (...) button.

The different verification types available in the selected strategy display in the **External Service Type Selection** dialog.
4. Select the types of verification that will run when the button is clicked, and then click **OK**.
5. If necessary, include the member code to verify in the **Member Code** field.

If no member code is specified, then the initiating member code is used.
6. Click **OK**.

Before attempting to use the Verify Member Address script action, make sure that the verification strategy is correctly configured. Any errors occurring during processing will display in a dialog, viewable by the user.

You can only select strategies with the same model and entity as the form uses. Strategies with a different context do not appear in the list.

## See Also

[Customize Context Buttons](https://support.profisee.com/wikis/profiseeplatform/customize_context_buttons)

[Add a Script Action to a Button in a Form Layout](https://support.profisee.com/wikis/profiseeplatform/add_script_action_form_button)

[Creating an Address Verification Strategy](https://support.profisee.com/wikis/profiseeplatform/create_an_address_verification_strategy)