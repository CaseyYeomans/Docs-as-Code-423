# Tab Navigation Script Action

The Tab Navigation script action opens a tab in the form when the user clicks the button.

To add the Tab Navigation script action to a button:

1. From the list of actions, select **Tab Navigation**, and then click **Add**.

The property displays in the Action Properties panel.
2. In the **Tab Index** field, enter the index value of the form tab to switch to.

The first tab in the form has a tab index of 1. Subsequent tabs are numbered sequentially. To switch focus to the fifth tab, you would use a Tab Index value of 5.

3. Click **OK**.

If no tab exists for the selected index value, nothing happens when the user clicks the button.

This script action is useful for controlling how users access other form tabs. When creating a form, you can clear the option to Render form with tabs visible. This means that only the first tab can be accessed by participants unless they click a button configured with the Tab Navigation script to access the hidden tabs.

## See Also

[Customize Context Buttons](https://support.profisee.com/wikis/profiseeplatform/customize_context_buttons)

[Add a Script Action to a Button in a Form Layout](https://support.profisee.com/wikis/profiseeplatform/add_script_action_form_button)