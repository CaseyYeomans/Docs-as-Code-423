# Refresh Member Script Action

The Refresh Member action refreshes the member indicated by the form when the user clicks the button.

When there are changes in a form and a user clicks a button configured to perform this action, the user is asked to confirm the refresh. If the user clicks yes, then the form retrieves all applicable values from the server. Otherwise, the Confirm Refresh dialog closes and the form remains in the current state.

If a user attempts to refresh a member that has not yet been saved to the database, the user will be prompted to confirm the refresh action. When a form containing an unsaved member is refreshed, the form is cleared and any changes are lost when the user confirms the refresh.

To add the Refresh Member script action to a button:

1. From the list of actions, select Refresh Member, and then click Add.
2. Click OK.

## See Also

[Customize Context Buttons](https://support.profisee.com/wikis/profiseeplatform/customize_context_buttons)

[Add a Script Action to a Button in a Form Layout](https://support.profisee.com/wikis/profiseeplatform/add_script_action_form_button)