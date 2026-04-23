# Deleting a Workflow

Before deleting a workflow, carefully consider the consequences. Deleting a workflow deletes the following information:

- The workflow
- All associated workflow versions
- All activities associated with the versions
- All service participants associated with the workflow
- All workflow instance information stored in the database
- All local instance information used for reporting
- All task assignment information used for reporting

To delete a workflow:

1. Open the Workflow Manager tab.
2. Select the workflow in the list.
3. Click **Delete** in the Workflow Activities toolbar.

The workflow is removed from the list.

You cannot delete a workflow with workflow instances that are currently running.

When a workflow is deleted, the history associated with the workflow is also removed. It is a best practice to disable a workflow instead of deleting it to preserve this information.