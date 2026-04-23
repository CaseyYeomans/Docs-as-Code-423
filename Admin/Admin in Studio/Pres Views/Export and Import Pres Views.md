# Export and Import Presentation Views

The Presentation Views feature area includes the option to export presentation views and then import them into the same server or other servers. This process provides a way to back up presentation views and to transport views between servers.

## Exporting Selected Presentation Views

To export one or more presentation views:

1. In the navigation panel, under Administration, click **Presentation Views**.
2. Select one or more views in the list.
3. In the Presentation Views toolbar, click **Import/Export**.
4. On the menu, click **Export**.
5. Browse to the file location to save the view files.
6. Click **OK**.

The presentation views are saved in the selected location with the view name and the file extension \*.presentationview.

## Import Selected Presentation Views

To import one or more presentation views:

1. In the navigation panel, under Administration, click **Presentation Views**.
2. In the Presentation Views toolbar, click **Import/Export**.
3. On the menu, click **Import**.
4. Browse to the file location where the presentation views are saved.
5. Select one or more presentation views to import.
6. Click **Open**.

The presentation views are added to the list.

If there is a metadata mismatch between an imported presentation view and the server model (such as when an attribute referenced in the view is missing in the model), the view imports successfully, but is flagged with a red exclamation point in the list. Hover your mouse pointer over the icon to view the issue, and then make the necessary changes.

To remove a row with a reference error, select the row, and then click **Delete**. Save the presentation view.

If a mismatch occurs, you must edit and re-save the presentation view, even after the issue is fixed in the model.

If you resolve a mismatch by adding a missing attribute to the model, you must also reselect the attribute in the presentation view before re-saving.