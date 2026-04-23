# Profisee Workflow Control Activities Overview

The **Profisee Workflow Control** activities that are available in the Visual Studio Toolbox provide the workflow designer the tools they need to control the lifecycle and flow of a workflow. These activities extend the basic control flow activities provided by the .Net Framework.

The table below lists the available activities and provides a summary of their functions and purpose. Refer to each activity in the table above for more specific usage and configuration details.

| | |
| --- | --- |
| **Activity** | **Description** |
| [IfThen](https://support.profisee.com/wikis/profiseeplatform/if_then) | This activity extends the basic workflow control activities with an **IfThen** activity. The standard WF **If** activity requires both an 'if' as well as an 'else' branch. The Profisee **IfThen** activity contains only an 'if' branch. |
| [InitiateWorkflow](https://support.profisee.com/wikis/profiseeplatform/initiate_workflow) | This activity must appear as the first activity within a Profisee workflow. It performs two basic functions: (1) validating that the [RecordDataContext](http://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type) argument passed to the workflow is appropriate for the workflow in question and (2) it stores the **InitiatingUser** argument passed to the workflow in global memory of the workflow for reporting purposes. |
| [InitiateTemplateWorkflow](https://support.profisee.com/wikis/profiseeplatform/InitiateTemplateWorkflow) | This activity initiates a workflow without specifying a model and entity. |
| [LogMessage](https://support.profisee.com/wikis/profiseeplatform/log_message) | This activity supports the ability to log messages to the system log for diagnostic purposes. |
| [ThrowException<T>](https://support.profisee.com/wikis/profiseeplatform/throw_exception) | This activity supports the ability to throw an exception from within the workflow. The type parameter, T, identifies the type of exception being thrown. |
| [TriggerInternalEvents](https://support.profisee.com/wikis/profiseeplatform/trigger_internal_events) | This activity allows a workflow to trigger a configured **Internal Event Scenario** thus causing a different workflow or other subscriber to be invoked. |
| [Webhook](https://support.profisee.com/wikis/profiseeplatform/Webhook) | This activity is a standard component of Profisee's workflow activities delivered via the SDK. The Webhook activity allows the Profisee platform to invoke custom code that runs outside the platform. |