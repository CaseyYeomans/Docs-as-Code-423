# Developing a Workflow

Developing a workflow is fundamentally a development exercise. Profisee's SDK provides templates and activities to make this easy. However, a basic grounding in Windows Workflow Foundation (WF) is recommended. For some basic resources to help understand WF, refer to the [Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/jj684582.aspx) documentation on the Microsoft Developer Network (MSDN).

The steps to developing a workflow are as follows:

1. Install the Profisee SDK Developer Tools package.
2. Install the workflow activities toolbox using Visual Studio.

The workflow activities toolbox can be found in the root folder where the Profisee SDK has been installed. The file name is Profisee.Services.Sdk.Workflow.PackageInstaller.vsix. This adds the Profisee-specific workflow activities to the toolbox in Visual Studio.

1. [Develop the workflow using Visual Studio](https://support.profisee.com/wikis/profiseeplatform/build_a_workflow_with_visual_studio). Use the Profisee workflow activities to perform MDM-specific data management functions.

You must develop and build the workflow outside of Profisee using Visual Studio. Many workflow features will not function correctly unless the workflow is properly designed. For additional information, refer to the SDK Developer Tools documentation for details on developing workflows.

1. [Build the workflow in Visual Studio](https://support.profisee.com/wikis/profiseeplatform/build_a_workflow_with_visual_studio).
2. [Register the workflow](https://support.profisee.com/wikis/profiseeplatform/registering_workflows).
3. Use Forms to [create one or more forms to use with the workflow.](https://support.profisee.com/wikis/profiseeplatform/create_a_new_form)
4. [Configure the workflow](https://support.profisee.com/wikis/profiseeplatform/configuring_workflows) and [workflow activities](https://support.profisee.com/wikis/profiseeplatform/configuring_and_assigning_workflow_activities_overview), and assign a workflow run-as user in Workflow Administration. Note that the workflow run-as user must have Unattended Authentication enabled in Users and Teams.

For task activities, include the forms to be used to contribute and approve data, then specify the users responsible for fulfilling those tasks.

At a minimum, each task in a workflow activity must have:

- A form used to complete the task
- One user to whom the task is assigned
- The maximum duration allowed for users to complete the task
- A specification of how email notifications of task assignments should be processed

Optionally, a task can include the following:

- A description to aid the assigned users in understanding the expectations of the assignment
- A target duration that can be used to establish goals and norms for completion of this type of task. The target duration should be less than the maximum duration.
- A priority of this task. This can be used in combination with the description and target duration to guide users in how respond to this task relative to other tasks the user may be assigned.

1. [Initiate the workflow](https://support.profisee.com/wikis/profiseeplatform/options_for_starting_workflows).