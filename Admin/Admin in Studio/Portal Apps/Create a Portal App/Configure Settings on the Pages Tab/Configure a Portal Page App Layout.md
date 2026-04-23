# Configure a Portal Page Application Layout

When creating a new portal application page or editing an existing one, you can configure a unique page layout for your application or use one of 16 customizable templates. The Portal Page Configuration feature allows you to organize zones within the portal, choose and configure the application controls, and customize the properties of the application page.

### Access Portal Page Configuration

**From a New Application Page**

1. Navigate to the **FastApps** tab in Profisee FastApp Studio.
2. Select the application for which you want to create a portal page, then click **Edit** in the toolbar. Alternatively, double click the application for which you want to create a portal page.
3. Click **New** in the application toolbar.
4. Select **Custom Layout** to begin with a blank page configuration, or select one of the provided templates.

**From an Existing Application Page**

1. Navigate to the **FastApps** tab in Profisee FastApp Studio.
2. Select the application for which you want to configure a portal page, then click **Edit** in the toolbar. Alternatively, double click the application for which you want to create a portal page.
3. Select the page you want to configure, then click **Edit** in the application toolbar. Alternatively, double click the page you want to configure.

If you want to rebuild this page, click the **Choose Template** button in the top-left of the window to select a template or start from a blank page configuration. If you choose a new layout with an equal or greater number of zones as your current layout, all controls will be preserved. Otherwise, some controls and all their associated links will be deleted.

### Add, Remove, or Link Controls

You can add controls to a blank zone within the Portal Page Configuration.

1. Click the **Add**icon inside a blank zone to open the control options dropdown.
2. Select one of the available control options.

You can also remove controls from the application page or link them to another set of controls.

1. Right click the name of the controls you want to alter to open the dropdown menu.
2. Select **Delete** or **Link to**.
3. If Link to is selected, choose another zone to link the selected controls to.

### Split, Resize, or Merge Zones

If desired, you can split a zone in half vertically or horizontally. This function preserves the original controls of the zone in one half and creates a blank zone in the other. Zones can be split as small as 7% of the application page.

1. Select the zone you want to split.
2. Click the **Split Vertical** or **Split Horizontal** button in the top-left of the window. Alternatively, right-click the selected zone and click either **Split Vertical** or **Split Horizontal**.

Similarly, you can manually resize a zone.

1. Click the space between two zones to highlight it.
2. Click and drag the area to resize the zones surrounding it.

You can also merge two zones into one larger zone.

1. Select the zone you want to merge.
2. Click the dropdown arrow next to **Merge** in the top-left of the window and select the direction of the zone you want to merge with. Alternatively, right-click the selected zone and click **Merge [Direction].**

If attempting to merge two zones that already have controls configured, you will receive a prompt asking you to confirm. If you select Yes, the selected zone will be preserved and the other will be deleted.

### Page Properties

You can configure the name and description of the application page. This information will appear on the portal as well as in Profisee FastApps Studio.

### Zone Properties

You can configure the way the header for this zone is displayed on the portal. The available display options are:

- Control name and icon
- Control name only
- Control icon only

### Control Properties

You can configure the properties of controls within your application page. Your configuration options vary depending on the type of controls you select.

For more details on the available controls, see [Configure FastApps Portal Page Controls](https://support.profisee.com/wikis/profiseeplatform/configure_fastapps_portal_page_controls).

Filter Properties

The following properties can be configured for filters.

- **Name**: The internal name displayed within the configuration window only
- **Label**: The name displayed for the filter within the portal application page
- **Domain-based attribute filter**: Allows the user to filter through a domain-based attribute
- **Domain entity**: Select the entity by which the filter operates
- **Drop-down format**: Configures the order in which code and name are displayed
- **Automatically choose input mode**: Automatically formats the filter as a dropdown menu or a new window depending on the threshold
- **Pop-up mode record threshold**: The number of members the filter entity can contain before the filter defaults to a new window
- **Always use pop-up mode**: Causes the filter to open a new window
- **Text input mode**: Enables a search function to filter members
- **Free-form attribute filter**: Allows the user to filter by inputting text or numbers
- **Text input mode**: Restricts the filter to text only
- **Numeric input mode**: Restricts the filter to numerals only
- **Decimal precision**: Sets the maximum number of decimal places allowed in an input
- **Date picker input mode**: Restricts the filter to date only
- **Include time**: Includes hour and minute in the date

#### Entity Grid Properties

The following properties can be configured for entity grids.

- **Name**: The name displayed on the portal
- **Entity**: The entity the grid displays
- **View**: The [presentation view](https://support.profisee.com/wikis/profiseeplatform/presentation_views_overview) the grid conforms to
- **Add member form**:The configured [Form](https://support.profisee.com/wikis/profiseeplatform/forms_overview) users can use to add new members
- **Open member form**: The configured [Form](https://support.profisee.com/wikis/profiseeplatform/forms_overview) users can use to view or edit pre-existing members

Entity grid options:

- **Can delete**: Allows users to delete members from the portal view
- **Matching strategy**: The matching strategy the grid conforms to
- **Enable hyperlink to raise match group control**: Allows users to navigate to match group control by directly clicking the match group within the entity grid. This setting is recommended.
- **Enable lookup-before-create**: Applies [lookup-before-create](https://support.profisee.com/wikis/profiseeplatform/lookup_before_create) to the matching strategy
- **Prohibit add if lookup-before-create fails**: If lookup-before-create fails when attempting to add a new member, no member will be added.

#### Report Viewer Properties

The following properties can be configured for report viewers.

- **Name**: The displayed name for the report viewer on the portal
- **URL**: The URL for the report viewer on the portal

#### Task List Properties

The following properties can be configured for task lists.

- **Name**: The displayed name for the task list on the portal
- **Configure columns to display on the task list**: From here you can configure which columns of the task list are displayed, the display names of the tasks, the width of the columns, and the order of the rows.

#### Hierarchy Properties

The following properties can be configured for hierarchies.

- **Name**:The displayed name of the hierarchy on the portal
- **Hierarchy**: The configured [hierarchy design](https://support.profisee.com/wikis/profiseeplatform/hierarchy_designer_overview) this hierarchy conforms to

### Links

This field displays the linked relationships between zones, including the direction which controls are linked. From here you can view link control information or remove links between zones. If desired, you can change the Receiving Field of a zone by selecting it, navigating to the Links field, and selecting the dropdown menu next to the receiving field for that zone.