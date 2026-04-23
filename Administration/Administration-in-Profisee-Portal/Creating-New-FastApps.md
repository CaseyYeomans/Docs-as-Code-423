# Creating New FastApps

You can create new FastApps from the **FastApps** page in the administration area of Profisee Portal.

**To create a new FastApp**:

1. Click the **+** icon in the toolbar on the FastApps page. The **Add New FastApp** dialog opens.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i36a48052a7a7107a.png)
2. Complete the following fields:
   * **Name** (required): Enter a unique name for your FastApp.
   * **Description**: Add an optional short description explaining the purpose of the FastApp.
   * **Icon** (required): Select an icon from the provided list, or click the **+** button to upload a custom icon file. You can remove a selected icon by clicking the **X** button.
3. Click **Continue** to open the FastApp configuration form.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i36c480a25657be37.png)

From here, the FastApp configuration form opens, allowing you to configure your FastApp using four tabs. Once you are finished making changes to the FastApp, click **Save** or **Save and Close** to finalize the changes.

## FastApp Configuration

### Overview Tab

The Overview tab displays the basic properties you configured when creating the FastApp. All fields are editable from this tab:

* **Name**: The FastApp's identifier
* **Description**: Optional descriptive text
* **Icon**: The visual icon representing the FastApp in the portal navigation. You can change this from the default FontAwesome icons provided, or upload a custom icon with the **+** button.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i66d1f59d9d0afcf.png)

### Menu Tab

The Menu tab allows you to configure the navigation items that will appear in the portal navigation bar when users access your FastApp. Each menu item can link to a page or serve as a folder containing sub-menu items.

To add a new menu item, click the **+** button in the grid header. Each menu item includes the following configuration options:

* **Name** (required): The menu item name that will appear in the portal navigation bar. Names must be unique within the FastApp.
* **Type**: Select the menu item type from the dropdown:
  + **Internal**: Links to a FastApp page designed within the portal
  + **External**: Links to an external website by providing a URL
  + **Folder**: Creates a top-level menu item that can contain sub-menu items. Folders display a +/- icon to expand or collapse their contents.
* **Page**: Select which page to display when this menu item is clicked.

You can reorder menu items by dragging them to the desired position and dropping them in place. Menu items can also be deleted using the row-level delete button if they are no longer needed.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i510115ecbab7817b.png)

### Pages Tab

The Pages tab displays all pages created for your FastApp. Two pages are created by default: **Home** and **Work**. The pages grid displays the following information:

* **Name**: The page name
* **Type**: The page type
* **Updated On**: The datetime the page was last edited
* **Updated By**: The last user who edited the page
* **Created On**: The datetime the page was created
* **Created By**: The user who created the page

You can right-click a page (or select a page and click the ellipsis) to access the following options:

* **Open**: Opens the page in the Page Designer for editing
* **Clone**: Creates a copy of the page
* **Delete**: Removes the page from the FastApp. This also deletes all menu items associated with the page.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic637aed906130da2.png)

You can also create a new page by clicking the **+** icon on the top right corner of this panel. For more information on creating pages, see [Creating FastApp Pages in Profisee Portal](https://support.profisee.com/wikis/profiseeplatform/creating_new_fastapps)**.**

### Teams Tab

The Teams tab allows you to control access to your FastApp. You can choose to allow all accounts access to the FastApp or restrict it to one or more predefined teams using a left-right selector.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i97da211d395c5a1a.png)



## Managing Invalid Metadata

If changes are made to the system that result in invalid metadata in a FastApp (such as deleting an entity or attribute that's referenced in a page), the FastApps grid will display a row-level validation indicator (!) with a tooltip describing the issue.

FastApps with metadata issues can still be opened and edited in the administration area, allowing you to fix any existing issues. However, portal users will not be able to access the FastApp until all metadata issues are resolved. This validation error also occurs when a control in a zone is not fully configured, preventing the page from being saved.

---