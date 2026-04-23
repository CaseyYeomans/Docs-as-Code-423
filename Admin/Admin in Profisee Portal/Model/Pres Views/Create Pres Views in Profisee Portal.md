# Creating Presentation Views in Profisee Portal

To create a new presentation view in Profisee Portal:

1. Navigate to the **Presentation View** tab in the Administration section of Profisee Portal.
2. Click the **+** icon to add a new presentation view.
![](https://profisee.magentrixcloud.com/sys/staticasset/read/file-if94a29b08e2cad81.png)
3. Enter a **Name** and **Description** for the presentation view, and select an **Entity** to associate with this presentation view.
4. Click **Continue**.
5. Edit the details for the presentation view in the **Overview**, **Columns**, **Filters**, and **Sort Columns** tabs, then click **Save** or **Save and Close** when finished to finalize the presentation view.

### Overview

The Overview tab allows you to set general view options for the presentation view.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i2734b945edf12f4c.png)

- **Display Format**: Determines the way the DBA values display in the entity grid. Options include:
- Code [Name]
- Name [Code]
- Name
- Code

It is recommended not to use the display format **Name** when blank values exist for Name.

- **Page Size**: Determines the default number of records that are displayed in the entity grid at once.
- **Show validation column**: If selected, this option includes the column containing member validation status in the entity grid control.
- **Use this view as the entity default**: If selected, this option makes this presentation view the default configuration for all entity grid controls that include the same entity.

When there is no default presentation view for an entity and no other view is selected, an "All Columns" view is generated when using the Data Browser.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i7ac5c7abf9dd513f.png)

A different presentation view can be selected for entities with a default presentation view. If there is only one presentation view for an entity, then that view is automatically the default view for that entity.

### Columns

The Columns view allows you to select attributes to display as columns and configure column display properties for this view. A presentation view must include at least one column. **Name** and **Code** are added by default, but can be removed.

Select attributes from the Available Attributes list (or Select All) to populate the Selected Attributes list. Attributes ordered in the list from top to bottom are displayed in the entity grid control from left to right. Once selected, you can edit the settings for the selected attributes.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id4e6293432357dfe.png)

- **Name**: The Name of the selected attribute (cannot be edited)
- **Column Label**: The way the attribute is displayed in the presentation view. This can be used to give an attribute a more user-friendly name if desired.
- **Quick Filter**: If selected, this option allows an attribute to be discoverable when a user uses the quick filter in this presentation view.
- **Display Width**: The display width (in pixels) for this attribute in the presentation view.

When the presentation view is deployed in Profisee FastApp portal, the first column in an entity grid is displayed as a hyperlink that opens the Open Member form for each row. Though this is not dependent on the attribute used, it is recommended to choose an attribute that can easily identify a member as the first column in the entity grid, such as the **Name** attribute.

If the attribute in the first column is a Link or Match Group attribute configured for hyperlink, the attribute will open to the associated link or match group control instead of the Open Member form.

### Filters

The Filters tab allows you to apply hidden filters to select specific records. Users cannot see or remove these filters.

For information on building entity grid filters, refer to the following topics:

- [Build an Entity Grid Filter](https://support.profisee.com/wikis/profiseeplatform/build_an_entity_grid_filter)
- [Multi-line Entity Grid Filters](https://support.profisee.com/wikis/profiseeplatform/multi_line_entity_grid_filters)
- [Filter Using Parent Attributes](https://support.profisee.com/wikis/profiseeplatform/filter_using_parent_attributes)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ie3e3b81bc779ba65.png)

Note that when exporting presentation views, the **Export All** button will export **all** presentation views even if a filter is applied to limit the presentation views that are displayed.

### Sort Columns

The Sort Columns tab allows you to select attributes to display as columns and configure column display properties for the view. You can use an attribute to sort the grid that will not display as a column in the portal page. You can re-sort columns in the entity grid control displayed in the browser.

Select attributes from the Available Attributes list (or Select All) to add them to the Selected Attributes list on the right. Arrange the sort order by reordering selected attributes in the right panel.

- Move attributes up and down in the list by clicking the up and down arrows.
- Move attributes to the top of list and to the bottom by clicking the paging arrows.
- Remove attributes from the list by selecting the attribute and then clicking Delete, or by clearing the selection in the Available attributes to sort panel.