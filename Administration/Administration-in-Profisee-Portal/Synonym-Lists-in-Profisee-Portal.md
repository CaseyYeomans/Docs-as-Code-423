# Synonym Lists in Profisee Portal

Profisee Portal users with Administrator privileges can manage Synonym Lists in Profisee Portal. Synonym Lists are used during matching processes to standardize variations of words and phrases, improving match accuracy. Using the **Synonyms** page in the **Match** section of the portal, you can create, edit, import, export, and manage synonym lists that define how terms should be replaced during matching operations.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic978ce0190e825c.png)

From here, a list of all created Synonym Lists is displayed with the following information:

* **Name**: The name given for the Synonym List
* **Created By**: The user who created this list
* **Created On**: The datetime the list was created
* **Updated By**: The last user who edited the list
* **Updated On**: The datetime the list was last edited

If desired, you can right-click a synonym list (or select multiple) in this list to bring up the context menu, allowing you to **Open**, **Clone**, **Export**, or **Delete** the selected synonym lists. The **Open** and **Clone** options are only available when a single list is selected.

You can also click the ellipsis menu at the top of the grid to access additional options:

* **Import Synonyms**: Import one or more synonym lists from a JSON file (for synonym lists from 2026.R1 or later) or from .MatchingSynonym files (for synonym lists after 2025.R2). Multiple lists can be included in a single JSON file.
* **Export (All)**: Export all synonym lists to a single JSON file containing all list definitions.

Synonym Length and Term Length fields are calculated automatically based on the character count in the Find and Replace fields.You can use the Quick Filter to search for specific items in the synonym list grid.

### Creating a New Synonym List

To create a new synonym list, click the **Add (+)** button at the top of the grid. A dialog will appear prompting you to enter a name for your new synonym list.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i22458d500121fdff.png)

Enter a descriptive name for your list and click **Continue** to proceed to the configuration form, or click **Cancel** to exit without creating a list.

### Configuring a Synonym List

Once you create or open a synonym list, you'll see the Synonym List Configuration Form where you can define the replacement rules for your list.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-if3cf0e3108be8ea0.png)

The configuration form includes the following options:

* **List Name**: The name of your synonym list. You can edit this field to rename the list at any time.
* **Remove repeating words**: When enabled, this option removes words that repeat consecutively (e.g., "John John Smith" becomes "John Smith"). This checkbox is disabled by default.

#### Adding Synonyms

The **Synonyms** grid allows you to define individual replacement rules. Click the **Add (+)** button to add a new row to the grid. Each row in the grid includes:

* **Find (Synonym)**: Enter the value to find in your data (e.g., "St", "Corp", "Inc").
* **Replace (Term)**: Enter the replacement value to use during matching (e.g., "Street", "Corporation", "Incorporated").
* **Search in String**: Check this box to search and replace the value anywhere within a string. If unchecked, the replacement will only occur when the value appears as a complete word. This is unchecked by default.
* **Priority**: Indicates the order in which replacements are applied. You can reorder synonyms by dragging rows up or down in the grid. If a word is replaced by a higher priority rule, that replacement will be used for subsequent rules down the list.

#### Deleting Synonyms

To delete a synonym row, hover over the row to reveal the **Delete (X)** button on the left side of the row, then click to remove it from the list.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-if699d77f75d763fc.png)

### Saving Your Changes

After configuring your synonym list, use the buttons at the bottom of the form to save your work:

* **Save**: Saves your changes and keeps the configuration form open for further editing.
* **Save and Close**: Saves your changes and returns you to the Synonyms grid.
* **Cancel**: Closes the form without saving any changes made since the last save.

The form displays the last updated date and time at the bottom to help you track when changes were made.

---