# Edit Entities

Edit an entity using Advanced Modeling:

1. Expand the model to the **Entities** container.
2. Do one of the following:

1. In the model tree, expand **Entities**.
2. In the model tree, right-click the entity you want to edit.
3. Click **Edit** on the menu, -**or-**
4. In the model tree, select **Entities**.
5. In the modeling grid, select the entity you want to edit.
6. Click the plus icon on the modeling grid toolbar.

The **Edit Entity** dialog appears.

3. Edit the entity as necessary:
- **Name**: The name of the entity
- **Description**: An optional description of the entity
- **Icon Name**: Reference an icon from [fontawesome.com](http://www.fontawesome.com) to represent this entity. See more below.
- **Create Code values automatically**: Generate code values for data members.
- **Starts with**: Used with the **Create Code values automatically** option. Determines the initial value when codes are generated automatically.
4. Click **Save**.

The edited entity appears in the tree view pane as a change. In the modeling grid, the edited entity appears shaded yellow. When the model is saved, the standard entity icon displays, and the shading in the grid disappears.

### Icon Configuration

You can reference an icon from [fontawesome.com](https://fontawesome.com/) to use as the display icon for this entity. This icon will also appear next to the entity in Hierarchy views in FastApp portal. To configure an icon, find a suitable image on [fontawesome.com](https://fontawesome.com/) and copy and paste the icon's class string in the **Icon Name** field. Note that when saving the configuration, the icon's class string will automatically change to the icon's base name. You can paste the copied HTML directly into the form and it will automatically strip out the unnecessary HTML on save (e.g. `fas fas-address-book`).![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i55fc401f7d6682.png)

## See Also

[Log Audit Information](https://support.profisee.com/wikis/profiseeplatform/log_audit_information)