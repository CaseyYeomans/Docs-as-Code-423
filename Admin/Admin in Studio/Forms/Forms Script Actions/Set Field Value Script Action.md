# Set Field Value Script Action

The Set Field Value script action assigns a value to an attribute when the user clicks the button.

To add the Set Field Value script action to a button:

1. From the list of actions, select **Set Field Value**, and then click **Add**.

The properties display in the Action Properties panel.
2. Click the **Attribute** list.

The list opens, displaying all attributes available in the form.
3. From the list, select the attribute to use with the action.
4. Click the **Value** field.
5. Enter a value for the selected attribute.
6. Click **OK**.

Note that any Date attributes must be in ISO format (YYYY-MM-DD).

If Value is set to a type of value that is incompatible with the attribute type, the action processes, but an error displays afterward.

You must have one or more field controls in your layout, or the list of attributes appears empty. The attributes for the fields in the form display in the list.

When the selected attribute is a DBA, the value must a valid code for an existing DBA value.

## See Also

[Customize Context Buttons](https://support.profisee.com/wikis/profiseeplatform/customize_context_buttons)

[Add a Script Action to a Button in a Form Layout](https://support.profisee.com/wikis/profiseeplatform/add_script_action_form_button)