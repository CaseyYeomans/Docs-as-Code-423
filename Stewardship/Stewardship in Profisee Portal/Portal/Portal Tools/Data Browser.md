# Using the Data Browser

The Data Browser allows a user to easily access data from the FastApp Portal homepage without needing to navigate through individual FastApps and entities. The Data Browser allows you to access your data from a search bar on the homepage, which is linked to all of your FastApps at once. You can also directly access and link to the Data Browser for a specified entity or hierarchy from a URL.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-icd97987584d7efd9.png)![]()![]()

Once searched, the Data Browser offers the same functionality as an entity grid or hierarchy list, allowing users to edit, clone, and delete records directly from the Data Browser. The Data Browser makes it much more efficient to collaborate with other users, as the URL can be directly shared to other data stewards with permissions to view the specified data.

If no default presentation view is specified, a user can [Export to Excel](https://support.profisee.com/wikis/profiseeplatform/downloading_an_entity_grid_as_an_excel_file) from the Data Browser with all attributes for the specified entity included within the entity grid (provided the user has permissions to view all attributes).

If no default form or default presentation view are configured, the new system generated form and presentation view displays all permission-allowed attributes.

### Access from the Search Bar

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i428f90ccfd345963.png)

You can access the Data Browser from the search bar on the Profisee Portal landing page (pictured above).

1. Type the name of the entity or hierarchy you want to browse within the search bar.
2. Click the specified entity or hierarchy you want to select from the auto-populated results. Note that entities and hierarchies are designated by different icons.
3. The Data Browser page appears with the selected data.

You can then copy the URL to directly share this Data Browser page with other data stewards.

### Access from a URL

You can access the Data Browser for a specified entity or hierarchy directly from a URL.

1. Add the endpoint */\_entity/[Entity name]* or */\_hierarchy/[Hierarchy name]*to the URL of your Portal instance. For example: *https://xxxx.profisee.com/xxxx/\_entity/sample\_entity*
2. Submit the URL to navigate to the data browser for that entity or hierarchy.
Note that the URL replaces the user-friendly name with a GUID to prevent broken links from occurring if the name of the entity changes later on.

Once this URL is generated, you can copy the URL to directly share this Data Browser page with other data stewards.

#### **Purview Deep Links**

You can also access a Data Browser URL from a connected Purview account. Navigate to the entity/hierarchy in Purview and copy the **View in Profisee** URL found at the bottom of the **Properties** tab.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic211f5c0f9813c48.png)