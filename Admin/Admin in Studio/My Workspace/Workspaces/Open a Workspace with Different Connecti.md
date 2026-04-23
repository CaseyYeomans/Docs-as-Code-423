# Open a Workspace with Different Connection Information

You can open a workspace that was saved with connection information that is different from your current connection. This can be helpful when creating workspaces in environments with multiple Profisee servers.

To open a saved workspace with a different connection than your current one:

1. Click **Open a workspace** on the main toolbar.
2. Navigate to the saved workspace file and select it.
3. Click **Open**.

The Connect to Profisee dialog appears.
4. Select one of the following:

Your current workspace closes and the selected workspace opens.

- **Connection in Workspace**

Connects to the server saved in the workspace and opens the workspace.
- **--or--**
- **Current Connection**

Open the context in the workspace using the currently connected server.

To use the connection in the workspace, a few conditions must be met:

If any of these conditions are not met, then you will not be prompted to use the saved server connection in the workspace.

- The setting **Always default to connection saved in workspace** is not selected.
- The server URL of the currently connected server is different than the connection saved in the workspace file.
- The **Open** option was used to open the workspace, not **Open Into**.