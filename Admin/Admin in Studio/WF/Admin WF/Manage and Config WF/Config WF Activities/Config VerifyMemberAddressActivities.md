# Configuring VerifyMemberAddressActivities

The VerifyMemberAddress activity in a workflow processes a strategy created in the Profisee Address Verification feature area for the member referenced in the master data context.

To configure the VerifyMemberAddress activity:

1. Open the [Workflow Configuration](https://support.profisee.com/wikis/profiseeplatform/configuring_workflows) window for a registered workflow.
2. Navigate to the **Details** tab.
3. Select the VerifyMemberAddress activity you want to configure.

#### Activity Field

The activity field displays the version of Profisee FastApps Studio in which the workflow was created. If the workflow was imported from a different version than the version of Profisee you are running, the workflow process may encounter errors. If the Assembly Version is a higher version than the instance of Profisee you are running, it is recommended you upgrade the platform before continuing.

If desired, a user can add a description to the task that will be displayed to the workflow participants in their notifications.

#### Address Verification Field

4. Enter the name of the verification strategy to process for the referenced member.
5. Click **Save** to apply changes to the activity.