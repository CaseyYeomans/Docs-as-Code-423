# Workflow Activities Overview

Activities are the engine that drives the automatic process of a workflow. An activity defines one specific action the workflow takes in its flow. For example, if the **ContributionTask**activity is added to a workflow and is followed by an **ApprovalTask** activity, the workflow will automatically prompt one or more assigned users (via a notification and through their Task List in the Portal) to make data changes to the associated member record. Once those changes are made, the workflow then automatically prompts assigned users to approve the changes made by the prior user(s).

When building a workflow, you have access to five Profisee toolbox categories that contain activities to build your workflow that interacts with the Profisee Platform. These toolbox categories are:

- [Profisee Workflow Control](https://support.profisee.com/wikis/profiseeplatform/profisee_workflow_control_overview)
- [Profisee Data Management](https://support.profisee.com/wikis/profiseeplatform/profisee_data_management_overview)
- [Profisee Task Management](https://support.profisee.com/wikis/profiseeplatform/profisee_task_management_overview)
- [Profisee Matching](https://support.profisee.com/wikis/profiseeplatform/profisee_matching_overview)
- [Profisee Address Verification](https://support.profisee.com/wikis/profiseeplatform/profisee_address_verification_overview)

You can add activities from these categories to your workflow by clicking and dragging them from their toolbox onto the workflow design surface. Once added, you can configure the properties of the activities inside the design environment.

Some workflow activities have environmental configuration that can be specified in Workflow Administration. Refer to [C](https://support.profisee.com/wikis/profiseeplatform/configuring_workflows)[onfiguring and Assigning Workflow Activities](https://support.profisee.com/wikis/profiseeplatform/configuring_and_assigning_workflow_activities_overview) for more details.