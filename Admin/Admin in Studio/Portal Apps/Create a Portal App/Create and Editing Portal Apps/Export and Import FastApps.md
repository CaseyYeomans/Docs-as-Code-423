# Export and Import FastApps

The Profisee FastApps feature includes the option to export portal applications and then import them into the same server or other servers. This process provides a way to back up portal applications and to transport applications between identical models on different servers.

## Exporting Selected FastApps

To export one or more FastApps:

1. In the navigation panel, under Administration, click **FastApps**.
2. Select one or more applications in the list.
3. In the Applications toolbar, click **Import/Export**.
4. On the menu, click **Export**.
5. Browse to the file location to save the application files.
6. Click **OK**.

The applications are saved in the selected location under *AppName\_yyyy\_dd\_MM\_HH\_mm\_ss* and the file extension \*.portalapplication.

## Importing Selected FastApps

**You must import all presentation views and forms used by the application before importing the application itself.**

To import one or more portal applications:

1. In the navigation panel, under Administration, click **FastApps**.
2. In the Applications toolbar, click **Import/Export**.
3. On the menu, click **Import**.
4. Browse to the file location where the applications are saved.
5. Select one or more applications to import.
6. Click **Open**.

The applications are added to the list.

If there is a metadata mismatch between an imported portal application and the associated model (such as when an attribute referenced in the portal application is missing in the model), the portal application imports successfully, but is flagged with a red exclamation point in the list. Hover your mouse pointer over the icon to view the issue, and then make the necessary changes.

If a mismatch occurs, the portal application must be opened and re-saved, even when the issue (such as a missing attribute) is fixed in the model.

After correcting missing information to resolve the mismatch, edit the application. Reselect the attribute, form or presentation view, and then save the application.