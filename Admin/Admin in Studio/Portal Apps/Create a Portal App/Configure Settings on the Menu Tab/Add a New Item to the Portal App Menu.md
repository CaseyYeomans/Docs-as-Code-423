# Add a New Item to the Portal Application Menu

The FastApps Portal application menu displays links for internal and external pages. The menu is associated with all internal pages included in the portal application.

1. In the navigation panel, under Administration, click **FastApps**.
2. Access the Menu tab, either by [editing an existing application](https://support.profisee.com/wikis/profiseeplatform/edit_menu_item) or [adding a new one](https://support.profisee.com/wikis/profiseeplatform/create_a_new_fastapp).
3. On the Menu tab, click **Edit** in the toolbar.

The information in the Menu tab grid is read only until you click **Edit**.

4. Click **Add** on the Menu tab toolbar.

A new row is added to the list of pages.
5. In the new row, enter the information for the menu for this portal application.

This information determines the way the menu items for this application display and function in the portal.

1. In the **Name** column, enter the text that should display for the FastApps application menu item.

The characters in the Name field allow users to recognize the application in the FastApps menu.

All page names, including the default page names, are editable.

2. In the **Icon** column, select the icon to be used for the item by inputting a name into the **Name** field and a [fontawesome class string](https://support.profisee.com/wikis/profiseeplatform/edit_entities) into the **Icon name** field.
3. In the **Type** column, select **Internal** if the page is included in the FastApps Portal application or **External** if the page is located on a different site.

When configuring an external page to the FastApp, it is important to use *https://* formatting before the URL to ensure proper conversion. E.g. *https://bing.com*.

4. In the **Page** column, select the page from the list to link with the menu item (for internal pages), or type the URL of the page to access (for external pages).

6. Click **Save** to save your changes.

Audit and Notification pages are included with the internal pages. These pages are not linked by default, but they are available to add to your FastApps Portal menu if you want to include them. The Notifications page includes a list of active task notifications for the current user, and the Audit page includes transaction information for the current context.