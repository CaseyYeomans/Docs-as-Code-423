# Copy and Paste Entities

Copying and pasting lets you reuse entities within the same model or between different models.

To copy and paste an entity using the tree view in Advanced Modeling:

1. Expand the model to the **Entities** container.
2. Expand **Entities**.
3. In the model tree, right-click the entity you want to copy.
4. Click **Copy** on the menu.

The entity is placed on the clipboard.
5. Right-click **Entities** in the destination model.
6. Click **Paste** on the menu.

The entity appears in the new location.

To copy and paste an entity using the modeling grid:

1. Expand the model to the **Entities** container.
2. In the model tree, select **Entities**.
3. Select the entity you want to copy in the modeling grid.
4. Right-click the entity and then click **Copy** on the menu.

The entity is placed on the clipboard.
5. In the model tree, navigate to the Entities container in the destination model.
6. Right-click the modeling grid.
7. Click **Paste** on the menu.

The Copy Entity dialog appears.
8. Make any changes to the entity using the dialog and then click **Save**.

When you copy entities, you may be prompted to copy dependent objects as well. If you want to make copies of all objects dependent on the selected entity and copy those, too, leave the boxes for the dependent objects selected.

Dependent objects are copied automatically for some objects, without prompting. This occurs in situations where the object cannot exist without the dependencies.

You can only copy objects to a relevant context.

You can copy multiple entities at a time by using CTRL+Click or SHIFT+Click.

If an entity contains a system-aware identity management (SAIM) attribute, the system identity property is not copied with that attribute when the entity is copied.