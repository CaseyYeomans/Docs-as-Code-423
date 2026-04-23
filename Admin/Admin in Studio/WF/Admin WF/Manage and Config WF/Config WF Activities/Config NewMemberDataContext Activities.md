# Configuring NewMemberDataContext Activities

The NewMemberDataContext allows a workflow to add additional data contexts beyond the context that triggered the workflow. These data contexts can be used to reference related data to the original context.

To configure the NewMemberDataContext activity:

1. Open the [Workflow Configuration](https://support.profisee.com/wikis/profiseeplatform/configuring_workflows) window for a registered workflow.
2. Navigate to the **Details** tab.
3. Select the NewMemberDataContext activity you want to configure.

#### Activity Field

The activity field displays the version of Profisee FastApps Studio in which the workflow was created. If the workflow was imported from a different version than the version of Profisee you are running, the workflow process may encounter errors. If the Assembly Version is a higher version than the instance of Profisee you are running, it is recommended you upgrade the platform before continuing.

If desired, a user can add a description to the task that will be displayed to the workflow participants in their notifications.

#### Member Context Field

4. Select the name of the entity in the new master data context
5. Click **Save** to apply changes to the activity.