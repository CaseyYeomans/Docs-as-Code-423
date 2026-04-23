# Export a Workflow

Profisee Workflow includes the option to export workflow configurations and then import them into the same server or other servers. This process provides a way to back up workflows and to transport them between different servers.

## Export Selected Workflows

To export one or more workflows:

1. In the navigation panel, under Administration, click **Workflow**.
2. Select a workflow in the list.

You can only export one workflow configuration at a time.

1. In the Workflow toolbar, click **Import/Export**.
2. On the menu, click **Export** to file.
3. Browse to the file location to save the workflow file.
4. Enter a name for the file, or use the default name provided.
5. Click **Save**.

The workflow is saved in the selected location with the file extension \*.workflow.

To see the specific information included in the exported file, see [Information Included in an Exported Workflow Configuration](https://support.profisee.com/wikis/profiseeplatform/exported_workflow_configuration).

## Export Workflows by Model

You can also choose to export all workflows that are configured for the same model. Workflows can involve multiple models; this option exports all workflows with the same model specified in the InitiateWorkflow activity. This activity is common to all Profisee workflows and is configured in Visual Studio during the development portion of workflow production.

To export all workflows for a selected model:

1. Navigate to **Administration | Workflow**.
2. On the Workflow toolbar, click **Import/Export**.
3. On the menu, click **Export** by model.
4. Select the model from the list.

If all workflows in the list refer to the same model, it's assumed that you want to use that model as a reference. There is no prompt to select a model.

1. Browse to the location to save the workflow files.
2. Click **OK**.

The workflows are saved in the selected location. Each workflow is saved to a separate file using the following naming convention:

*workflowName-timeAndDateExported*.workflow.