# Creating and Configuring Forms

You can create new forms from the **Forms** page in the administration area of Profisee Portal. Forms define how data is displayed and edited for entities throughout the portal, providing a customizable interface for data entry and record management.

To create a new form:

1. Click the **Plus (+)** icon in the toolbar on the Forms page. The **Add New Form** dialog opens.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i8da2870cc06db8b6.png)
2. Complete the following fields to configure the basic properties of your form:
   * **Name** (required): Enter a descriptive name for your form.
   * **Entity** (required): Select the entity this form will be associated with from the dropdown menu.
   * **Form Title**: Specify the title that will be displayed at the top of the form.
   * **Description**: Add an optional description to explain the purpose of this form.
   * **Show tabs on form**: Check this box to display tabs on the form. When enabled, you can create multiple tab layouts to organize form elements into logical sections.
   * **Use this form as the default for the entity**: Check this box to set this form as the default form that appears when users view or edit records for this entity.
   * **Set Form Width as % or Fixed (px)**: Choose whether the form width should be a percentage of the available space or a fixed pixel width, then enter the desired value.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-icbc9c6f68712b5b3.png)
3. Click **Continue** to open the Form Designer.

From here, the Form Designer opens, allowing you to build and configure your form using three main areas. Once you are finished making changes to the form, click **Save** or **Save and Close** to finalize the changes.

## Form Designer

The Form Designer consists of three main areas that work together to provide a complete form-building experience:

* **Form Layout** (left panel): A hierarchical tree view of all form elements and tabs.
* **Form Properties** (center panel): Configuration options for the selected element.
* **Form Preview** (right panel): A real-time preview of how the form will appear to users.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibcbc7d1e1c768983.png)

### Configuring Form Properties

When you select the Form element at the top of the Form Layout tree, the Form Properties panel displays two tabs: **General** and **Context Buttons**.

#### General Tab

The General tab displays the same basic properties you configured when creating the form. You can modify any of these properties at any time:

* **Name**: The form's identifier
* **Entity**: The associated entity (read-only)
* **Title**: The display title for the form
* **Description**: Optional descriptive text
* **Show tabs on form**: Controls tab visibility
* **Use this form as the default for the entity**: Sets default form status
* **Set Form Width as % or Fixed (px)**: Controls form width behavior

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i47a50c33cec85a09.png)

#### Context Buttons Tab

The Context Buttons tab allows you to customize the action buttons that appear on the form for different tasks. You can configure buttons for the following scenarios:

* **Save And Continue Task**: Configure the button for saving and continuing to the next step
* **Save Task**: Set the button for saving the current record
* **Approve Task**: Define the button for approving a record
* **Reject Task**: Configure the button for rejecting a record
* **Add Member**: Set the button for adding a new member record
* **Add Member And Close**: Define the button for adding a member and closing the form
* **Update Member**: Configure the button for updating an existing member
* **Update Member And Close**: Set the button for updating a member and closing the form

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i58bf3dc463e02612.png)

### Managing Tabs

Tabs allow you to organize form elements into logical sections, making complex forms easier to navigate. Tabs are displayed at the top of the Form Preview and can be managed through the Form Layout panel.

#### Adding Tabs

To add a new tab, right-click on the Form element or an existing Tab Layout in the Form Layout tree and select **Add tab layout**. New tabs are automatically named "Tab [number]" based on the tab count (e.g., Tab 1, Tab 2). You can also right click the form name and select **Add multiple tabs** to create several tabs at once.

> [!NOTE]
> Note: You must have the Show tabs on form checkbox enabled to create multiple tabs. If this option is unchecked, only the first tab will be visible in the Form Preview.

#### Renaming Tabs

To rename a tab, click on the tab layout element in the Form Layout tree to select it. In the Form Properties panel, update the **Label** field under the Display section. The change will immediately appear in both the Form Layout tree and the Form Preview.

#### Reordering Tabs

You can reorder tabs using drag-and-drop in the Form Layout tree. Click and hold on a tab layout element, then drag it to the desired position.

#### Deleting Tabs

To delete a tab, right-click on the tab layout element in the Form Layout tree and select **Delete**.

> [!NOTE]
> Important: If you have multiple tabs created and then uncheck the Show tabs on form option, only the first tab (left to right) will remain visible in the form.

### Building Form Layout with Elements

The Form Layout panel displays a hierarchical tree of all elements in your form. You can add various types of form elements by right-clicking on a tab layout or other container element and selecting from the available options.

#### Available Form Elements

The following elements can be added to your form:

* **Field**: Adds a single attribute field for data entry
* **Multi-level attribute**: Adds a field that displays related entity data
* **Relationship list**: Displays records from a related entity
* **Layout grid**: Creates a container for organizing multiple fields in rows and columns
* **Button panel**: Adds a container for grouping action buttons
* **Button**: Adds an individual action button
* **Label**: Adds text labels for organizing form sections
* **Match group**: Displays matching and clustering information
* **Blank**: Adds empty space for layout purposes
* **Hierarchy**: Displays hierarchical entity relationships

#### Configuring Element Properties

When you click on any element in the Form Layout tree, its properties appear in the Form Properties panel. The properties panel slides out over the Form Preview and can remain open as you select different elements, allowing you to quickly configure multiple elements.

Each element type has its own set of properties that control its behavior and appearance. For example, when configuring a Field element, you can set:

* **Attribute**: Select which entity attribute this field represents
* **Behavior**: Control AI Role, enabled state, enabled conditions, and validation
* **Display**: Configure display format, label text, label styling (bold, color, italic, size, underline)
* **Layout**: Set positioning and sizing options

#### Organizing Elements

You can reorganize form elements using drag-and-drop in the Form Layout tree. Click and hold on an element, then drag it to a new position. Elements can be moved within the same container, between different containers, or even between tabs.

Additionally, you can use the context menu to **Copy** and **Paste** elements. Right-click an element and select Copy, then right-click on the destination location and select Paste.

> [!NOTE]
> The Paste option only appears in the context menu when you have previously copied an eligible element.

### Using the Form Preview

The Form Preview panel on the right side of the Form Designer provides a real-time view of how your form will appear to users. As you add elements, configure properties, or make layout changes, the preview updates immediately to reflect your modifications.

You can interact with the preview by clicking on different tabs to switch between tab layouts, which automatically updates both the Form Preview and the Form Layout tree to show the selected tab's elements.

### Saving Your Form

After building and configuring your form, use the buttons at the bottom of the Form Designer to save your work:

* **Save**: Saves your changes and keeps the Form Designer open for further editing.
* **Save and Close**: Saves your changes and returns you to the Forms grid.
* **Cancel**: Closes the Form Designer without saving any changes made since the last save.

The designer displays the last updated date and time at the bottom to help you track when changes were made.

---