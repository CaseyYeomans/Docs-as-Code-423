# Workflow FAQ

The following are answers to frequently asked questions about Workflows:

- Will a workflow instance automatically restart if there is a communication loss to the workflow host?

If the service or app pool are down, workflow features will not properly function. Any attempt to complete a task before the app pool restarts may cause workflows not to perform as expected.

If communication to the host is lost, you should manually refresh the workflow page in Profisee FastApp Studio before attempting to complete a task to ensure the app pool is running.