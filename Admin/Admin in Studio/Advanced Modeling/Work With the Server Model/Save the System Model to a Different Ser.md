# Save the System Model to a Different Server

Open the system model from one server, edit the model using Advanced Modeling, and then save that model to a second server. This lets you use the existing model as a template for other servers, as well as move model changes from a development or test environment to a production server.

1. Open the system model in the modeling surface.

1. From the Advanced Modeling tab, click **Open** in the modeling toolbar.
2. Select **Open from Server** on the menu.

The model opens in the tree view pane of the Advanced Modeling tab.
2. Make any necessary changes to the model.
3. Save the model as a file and close the model.
4. Connect to a different server.

1. Click **Connect** on the main toolbar.
2. Select the second server connection on the menu.
3. Click **Connect**.
5. Open the saved model file.
6. Click **Publish to Server** on the modeling toolbar.
7. Resolve any conflicts, making sure that the metadata from the saved model replaces the existing metadata in the system model on the target server.

For more information, see [Resolve conflicts](https://support.profisee.com/wikis/profiseeplatform/resolve_conflicts).
8. Click **Publish**.

The model is now available on the second server.