# Options for Starting Workflows

Data management solution designers have several options for starting workflows to run on a specific master data record. This article covers the typical approaches to starting a workflow as needs dictate.

### Starting Workflows based on Data Changes

The most common approach to starting workflows is using the platform's Real Time Event Processing subsystem. In this approach, the platform's Workflow Subscriber monitors data changes using a Subscriber Configuration that identifies the workflow to start, then uses an Internal Event Scenario that specifies the type of data changes that should cause the workflow to start. See [Create a Configuration for the Workflow Subscriber](http://support.profisee.com/wikis/profiseeplatform/create_a_configuration_for_the_workflow_subscriber)and [Create an Event Scenario for the Workflow Subscriber](https://support.profisee.com/wikis/profiseeplatform/create_workflow_event_scenario) for detailed setup instructions.

### Starting Workflows using Portal Form Script Actions

A user can design a FastApp Portal Form to start workflows by configuring Script Actions associated with various Context Buttons associated with the Form. There are two Script Actions that can be used to start a workflow:

- The **Trigger Internal Event** Script Action can be used to start a workflow indirectly by triggering an on-demand event associated with the Workflow Subscriber through the Real Time Event Processing system as described above.
- The **Initiate Workflow** Script Action can be used to start a workflow by causing the Form to make an explicit request to the Workflow Service to start an instance of the identified workflow.

See [Trigger Internal Event Script Action](https://support.profisee.com/wikis/profiseeplatform/TriggerInternalEventAction) and [Initiate Workflow Script Action](https://support.profisee.com/wikis/profiseeplatform/initiate_workflow_script_action) for detailed setup instructions.

### Starting Workflows from a Workflow Instance

Workflow designers can start other workflows by using the **TriggerInternalEvents** activity. This workflow activity will trigger an on-demand event through the Real Time Event Processing subsystem. If that on-demand event is associated with a different workflow, then instances of the associated workflow are started. For details, refer to the [TriggerInternalEvents Activity](https://support.profisee.com/wikis/profiseeplatform/trigger_internal_events) under [Profisee Data Management](https://support.profisee.com/wikis/profiseeplatform/profisee_data_management_overview) activities.

### Starting Workflows Manually

Users can start a workflow manually from the Workflow Administration using FastApp Studio. Refer to [Manually Initiating Workflows](https://support.profisee.com/wikis/profiseeplatform/manually_initiating_workflows) for specific steps.