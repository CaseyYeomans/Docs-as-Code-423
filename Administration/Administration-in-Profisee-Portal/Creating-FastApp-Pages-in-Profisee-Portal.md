# Creating FastApp Pages in Profisee Portal

## Creating and Designing Pages

To create a new FastApp page, click the **+** button in the Pages tab grid. The Page Designer opens, providing a flexible canvas for building your page layout.

### Page Designer Overview

The Page Designer consists of three main areas:

* **Page Properties** (top): Configure the page name and description
* **Page Preview** (center): Visual representation of your page layout with configurable zones
* **Add Control Panel** (right): List of available controls to add to your page zones

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i76cf3d49bf95fd42.png)

### Configuring Page Layout

The Page Designer starts with a single zone that can be customized to create your desired layout. To modify the layout, right-click within a zone to access options for splitting or merging zones:

* **Split Up/Down**: Divides the zone horizontally, creating two zones stacked vertically
* **Split Left/Right**: Divides the zone vertically, creating two zones side by side
* **Delete Zone**: Removes a zone from the layout. If the zone is not empty, you will receive a warning.

Continue splitting zones until you achieve your desired page layout. Zones can also be merged by deleting adjacent zones and resizing remaining zones as needed.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iff2b08f7451bd7ea.png)

### Adding Controls to Zones

Click within any zone to open the control menu and select from the following control types:

* [**Entity Grid**](https://support.profisee.com/wikis/profiseeplatform/entity_grid_control): Display and interact with entity data in a grid format
* [**Filter**](https://support.profisee.com/wikis/profiseeplatform/filter_dba_control): Provide filtering options using dropdown, visual, or text input interfaces
* [**Free-Form**](https://support.profisee.com/wikis/profiseeplatform/filter_freeform_control): Allows users to filter using any custom value.
* [**Hierarchy**](https://support.profisee.com/wikis/profiseeplatform/hierarchy_control_portal): Display hierarchical entity relationships
* [**Report Viewer**](https://support.profisee.com/wikis/profiseeplatform/report_viewer_control): Embed external reports by URL
* [**Task List**](https://support.profisee.com/wikis/profiseeplatform/task_list_control): Display and manage workflow tasks

Once a control has been added to a zone, you can drag and drop it to a different zone. If the target zone already contains a control, the controls will switch places.

## Linking Controls

Once added to a zone, filter and entity grid controls can be linked to other controls to create interactive, connected experiences. Controls are linked using the **Link to** option on a selected control.

When two controls are linked, there is always a sending control and a receiving control:

* The **sending control** provides configuration information for a sending attribute.
* The **receiving control** receives this configuration and applies the filter or other logic.

For example, you can configure a filter control to use the Color domain attribute. The filter control sends the filter values—the attribute (Color) and associated options like display and input interface—to the receiving control, linking the appropriate entity in the receiving zone (such as Product).

After the entity is linked, configure a receiving attribute in the **Links** panel. Only valid attributes will appear in the list. When a receiving attribute is selected, it receives the filter information and applies the filter control to the selected attribute in the entity grid.

> [!NOTE]
> You can only link Filter to Grid, Filter to Filter, or Grid to Grid.

## Saving Your Page

After configuring your Page and designing its pages, use the buttons at the bottom of the form to save your work:

* **Save**: Saves your changes and keeps the Page form open for further editing
* **Save and Close**: Saves your changes and returns you to the Page grid
* **Cancel**: Closes the form without saving any changes made since the last save

---