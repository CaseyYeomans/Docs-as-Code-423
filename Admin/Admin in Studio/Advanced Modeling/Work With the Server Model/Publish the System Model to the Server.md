# Publish the System Model to the Server

Publishing model metadata using Advanced Modeling applies the metadata changes to the system model. Any metadata not present in the system model is deleted, so it is important to carefully review the information in the Publish to Server dialog before applying the changes.

**IMPORTANT**: When you publish the edited model with Replace the model selected, any changes you have made are applied to the version on the server. This includes any attributes that you have added, deleted or changed. If you have deleted an entity or attribute, or altered a data type, you could lose existing data in a populated model that has been modified.

To publish the system model to the server:

1. In the tree view pane, select the model that you want to publish.
2. Click **Publish to Server** on the modeling toolbar.
3. Select the publishing option, **-or-**

- **Merge models**

Adds to and updates the server model with the changes in the selected model open in the modeling surface.
- **Replace the model**

Deletes the server model and replaces it with the model in the modeling surface.
4. Review the changes to the model.

Before you publish the model to the server, Advanced Modeling compares the source (local edited version) model with the target (server model). The changes display in the Publish to Server dialog. Check the changes carefully to make sure that these are the changes that you want to apply.

By default, only the changes display. To view the whole model, clear the Show changes only option. For more information on changes, see [Review changes in published models](https://support.profisee.com/wikis/profiseeplatform/review_changes_in_published_models).
5. Resolve any conflicts.

For more information, see [Resolve conflicts](https://support.profisee.com/wikis/profiseeplatform/resolve_conflicts).
6. Click **Publish**.

The model is published to the server.

You can open the server model without checking out the model. However, you must check out the model before you publish your changes back to the server. If you prefer, you can wait to check out until you are prompted to do so during the publishing step.

If you delete entities, attributes or any parts of a model that are in use and contain data, that data is deleted when the model is published to the server.

If your published changes involve deletions, you are prompted to sign a Data Deletion Acknowledgment before the objects are deleted. There is one acknowledgment form for all deletions per publishing action. If you want to review the deletions individually before you publish, cancel the Data Deletion Acknowledgement and review the changes in the Publish to Server dialog.

If you are publishing modeling changes to a production model on a server, review the changes in the Publish dialog carefully before you complete the publishing process. When changes are published, they are active immediately. Any users currently accessing the system will be affected.