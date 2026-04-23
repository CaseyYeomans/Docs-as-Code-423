# Resolve Conflicts

Before Advanced Modeling publishes changes to the system model on the server, it first compares the source model to the existing model. The publishing function checks to make sure that, when the changes are applied, there will be no logical inconsistencies on the server. An example of an inconsistency is attempting to publish an entity with the same name but a different Globally Unique Identifier (GUID) to an entity that already exists in the server model.

Profisee first alerts you to the existence of these inconsistencies and then lets you decide how to resolve them before the model is published, ensuring that the publishing process does not fail.

To resolve conflicts:

1. Select the model that you want to publish.
2. Click **Publish to Server** on the modeling toolbar.
3. Select the publishing option**:**

- **Merge models**

Adds to and updates the server model with the changes in the selected model open in the modeling surface.

**--or--**

- **Replace the model**

Deletes the server model and replaces it with the model in the modeling surface.

4. Click **Next Conflict** at the top of the dialog.

The first change in the model where there is a conflict is highlighted.

If there are no conflicts, then the **Next Conflict** and **Previous Conflict** options will not be enabled.

5. Right-click the highlighted object.
6. Select **Resolve Conflict** on the menu.

You can also select **Skip** for any change where there is a conflict. Advanced Modeling does not attempt to publish skipped changes.
7. Select the way you prefer to resolve the conflict.

Options may include renaming an object, or changing a mapping.
8. Continue working through the conflicts using **Next Conflict** and **Previous Conflict** until no further conflicts remain.
9. Click **Publish**.

The model publishes, updating changed objects in the target model according to user selections.

For more information on types of conflicts, see [Conflicts and resolutions](https://support.profisee.com/wikis/profiseeplatform/conflicts_and_resolutions).