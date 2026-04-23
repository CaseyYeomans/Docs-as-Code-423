# Configuring Workflows

After a workflow is registered, it must be configured to notify users and save updated member data. Configure your workflow after you have created one or more forms to use with it. For more information on forms, see [Forms overview](https://support.profisee.com/wikis/profiseeplatform/forms_overview).

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i726f3e86d6b4cc7c.png)

To configure a workflow:

1. Expand the workflow you want to configure within the Workflow Manager tab.
2. Select the workflow version under the workflow.
3. On the Workflow Manager toolbar, click **Edit workflow version configuration**. Alternatively, right-click the workflow version and select **Edit Configuration**.

If the workflow is a template workflow, you can create different configurations for various entities by clicking the **New**button under **Entity configuration** and selecting the entity defined for this workflow.

If the workflow is not a template workflow, the workflow will have a single configuration for the entity defined for the workflow. You cannot add additional entity configurations for non-template workflows.

The Workflow Configuration dialog appears.

4. Review the following information about this version of the workflow:

**Name**: The name of the workflow
*NOTE: Administration behavior currently sets the Workflow Version Configuration Name to "{EntityName} Workflow", but a user can change this. Persisting multiple workflow versions with the same name may produce undesirable results with reporting.*

**Version**: The version of the workflow

**Run-as User:** The account that runs the workflow

Ensure the run-as user has been assigned all required permissions directly or through a team. Run-as users require [unattended authentication](https://support.profisee.com/wikis/profiseeplatform/edit_accounts) for use with workflows. Permissions inherited from an AD group are ignored when running a workflow on behalf of another user.

If no run-as user is selected, you cannot save your workflow configuration.![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-ibd01e5fbc8331f61.png)

**Total Activities**: The number of different assignment steps included in the workflow

**Total Assigned Users**: The number of users that can perform tasks in the workflow. This information comes from the Details tab.

**Target Duration**: An optional editable field and list defining the goal completion time for the workflow. This setting represents a service-level agreement (SLA) and can assist in defining data governance process metrics. This setting applies to the selected workflow version.

The limits for the Target Duration value are as follows:

| Scale | Limit |
| --- | --- |
| Weeks | 52 |
| Days | 365 |
| Hours | 86,400 |
| Minutes | 525,600 |
| Seconds | 31,536,000 |

Enter the number of time scale units in the field, and then select the time scale units to use from the list. Scale selections include:

- **Seconds**
- **Minutes**
- **Hours**
- **Days**
- **Weeks**

**Description**: An optional editable field where you can add descriptive text.

Name, ID, Version, and Total Activities are coded into the workflow during development in Visual Studio.

5. Select an activity within the **Activity configuration** panel and configure the settings as desired.

The information required to configure an activity depends upon the type of activity. For specific details on configuring activity types, see [Configuring and Assigning Workflow Activities](https://support.profisee.com/wikis/profiseeplatform/configuring_and_assigning_workflow_activities_overview).
6. Repeat the previous step for each activity in the workflow.
7. Click the **Enabled or Disabled** button to enable or disable the workflow.

When a workflow is disabled, instances of the workflow are not triggered in response to the data changes specified in the associated workflow subscriber configuration. However, users can continue to perform tasks in currently running instances of the disabled workflow.
8. Click **Save**.