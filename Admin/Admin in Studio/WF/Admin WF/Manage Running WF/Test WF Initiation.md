# Test Workflow Initiation

Participant groups let you create groups of Profisee users and teams who can respond to workflow tasks based on argument value often determined at workflow runtime based on the data being processed. This approach provides a level of data-driven flexibility when assigning users to tasks. As an example, a workflow could use the country code associated with a customer record to direct tasks to a group of data stewards that handle customers headquartered in that country.

After you have created participant groups for an activity, you can select the group you want to notify by assigning it to ParticipantAssignmentArgument in the workflow code.

Participant groups are limited to the activity where they are assigned and are not available for reuse in other activities.

To edit a workflow participant group:

1. On the Workflow Manager tab, expand the workflow.
2. Select the version under the workflow.
3. On the Workflow Manager toolbar, click **Edit workflow version configuration**.

The Workflow Configuration dialog appears.
4. On the Details tab of the Workflow Configuration dialog, select the activity.
5. Click inside the Participant Assignment row, and then click the ellipsis (...).

The Participant Assignment dialog appears.
6. Click the Argument Value menu.
7. Select the participant group you want to edit from the list of groups.
8. Click the right arrow to add selected teams and users to the Selected Participants panel.
9. To remove a selected participant, select the team or user to remove, and then click the left arrow.
10. To save the selected members as a group:
11. Click **OK** to save the edited group.