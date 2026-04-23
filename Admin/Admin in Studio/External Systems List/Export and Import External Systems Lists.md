# Export and Import External Systems Lists

## Exporting the Systems List

To export the systems list:

1. In the navigation panel, under Administration, click **External Systems List**.
2. In the toolbar, open the **Import/Export** menu.
3. On the menu, click **Export**.
4. Browse to the location to save the list, and enter a name for the file.
5. Click **Save**.

The list is saved in the selected location with the default name External System and the file extension \*.externalsystemlist.

## Importing a Systems List

To import a systems list:

1. In the navigation panel, under Administration, click **External Systems List**.
2. In the toolbar, open the **Import/Export** menu.
3. On the menu, click **Import**.
4. Browse to the saved list location.
5. Select the list you want to import.
6. Click **Open**.

The external systems list opens in the External Systems List tab.

- Any new systems in the imported list are added to the list.
- Changes to any existing systems overwrite existing list items.
- Systems in the list that are in use (linked to an attribute) cannot be changed.
- Names of systems must be unique in the list. When a system is imported that matches an existing system by GUID, the existing system is updated, when possible. If an imported system matches an existing system by name, but not by GUID, then the new system is imported, and "Copy of" is added to the name so that it is unique.