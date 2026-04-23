# Using the Fabric Toolbar and Explorer

While performing Data Modeling and Data Stewardship tasks within Fabric, the Toolbar and the Explorer are useful tools for easily finding, filtering, and refreshing the Profisee instance. The Toolbar and Explorer views are visible at all parts of the data management process. Some features (such as Delete) may be disabled based on your permissions.

## Toolbar

The Toolbar contains the following features.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5675ffb6209f85b9.png)

### Artifact Settings

The Settings button allows you to view and edit settings for this Profisee instance, based on your permissions.

### Save Changes

The Save Changes button allows you to save all changes made to the Profisee instance.

### Delete

The Delete button can be used while a record is highlighted to delete that record

### Search

The Search bar can be used to search for records and entities that exist within this Profisee instance based on keywords. You can click artifacts that appear in the search dropdown list to navigate to them directly.

### Edit a Record

The Edit a Record button can be used to open the [Edit Record](https://support.profisee.com/wikis/profiseeplatform/using_fabric_for_data_stewardship) pane.

### Filter Records

The Filter button allows you to Filter/Sort based on user-specified criteria. You can build one or more expressions by which to specifically filter data contained within the currently selected entity. These expressions are created using **Attributes**, **Operators**, and **Values**.

- **Attribute**: The attribute within the entity you want to filter
- **Operator**: A set of conditions by which to filter your attribute (Contains, is greater than, is between, etc.)
- **Value**: A plaintext field to set the value for your operator
- **And/Or**: Determines if additional expressions are And'd or Or'd (only appears on secondary expressions)

A completed expression may resemble: *Cost (attribute) is greater than (operator) $15 (value)*. You can click the Add new clause button to add additional expressions to your search criteria.

The Filter/Sort dialogue also includes a toolbar that allows you to edit your expressions. These tools include the following:

- **Add**: Adds a blank secondary expression to the Expression Builder
- **Delete**: Deletes a selected secondary expression
- **Move up**: Moves the selected expression(s) one row higher
- **Move down**: Moves the selected expression(s) one row lower
- **Group**: Groups two or more selected expressions (shift + click to select multiple). Grouped expressions are treated as a single expression when being moved or deleted.
- **Ungroup**: Returns a grouped expression to individual expressions
- **Delete all**: Deletes all expressions

Once all expressions have been created, click **Save** to filter the entity grid based on your selections.

### Reload

The Reload button allows you to refresh the Profisee instance, viewing the most up to date version of the instance and allowing you to see changes made by other Profisee users.

## Explorer

The **Explorer**is a navigational tool that allows you to open and close folders containing multiple entities, or use the Filter and Search features (described above). You can collapse or expand the Explorer by clicking the double-arrow icon on the top-right of the Explorer pane.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i8bc522a911480780.png)