# Edit a Presentation View

A user can edit a presentation view to sort the displayed grid as desired.

To edit a presentation view:

1. In the navigation panel, under Administration, click **Presentation Views**.
2. Select the view in the list.
3. In the toolbar, click **Edit**.

The Presentation Views edit panel opens.
4. To edit the view Name or Description, click **Edit**.
5. Edit the information on the **Columns** tab.

A presentation view must include at least one column (attribute).

1. Select the columns to display in an entity control by selecting attributes from the list from the left panel.

- Click **Select All** to select all of the attributes.
- Click **Clear All** to clear all attribute selections.
- Select individual attributes to add them one at a time.
- Expand a DBA and select one or more attributes beneath it to make a multi-level attribute selection.

For more information, see [Understand Parent Attributes](https://support.profisee.com/wikis/profiseeplatform/understand_parent_attributes).
2. Arrange the attribute order in the right panel.

Attributes ordered in the list from top to bottom display in the entity grid control from left to right.

- Move attributes up and down in the list by clicking the up and down arrows.
- Move attributes to the top of list and to the bottom by clicking the paging arrows.
- Remove attributes from the list by selecting the attribute and then clicking **Delete**, or by clearing the selection in the **Available attributes to display** panel.
3. Change the **Column Label** for each grid column that should display a user friendly name instead of the attribute name.
4. Select the attributes that will be examined when a user in the portal uses the [Quick Filter](https://support.profisee.com/wikis/profiseeplatform/use_the_quick_filter). The Quick Filter box is checked for Name and Code attributes by default, and it can be applied to any free form text or link attribute, DBA, or MLA that is related to the main entity.
5. Where necessary, change the default **Display Width** for each column.

The Display Width is in pixels.

When the presentation view is deployed in Profisee FastApp portal, the first column in an entity grid is displayed as a hyperlink that opens the Open Member form for each row. Though this is not dependent on the attribute used, it is recommended to choose an attribute that can easily identify a member as the first column in the entity grid, such as the **Name** attribute.

If the attribute in the first column is a Link or Match Group attribute configured for hyperlink, the attribute will open to the associated link or match group control instead of the Open Member form.

6. Edit the information on the **Filters** tab.

For information on building entity grid filters, refer to the following topics:

[Build an Entity Grid Filter](https://support.profisee.com/wikis/profiseeplatform/build_an_entity_grid_filter)

[Multi-line Entity Grid Filters](https://support.profisee.com/wikis/profiseeplatform/multi_line_entity_grid_filters)

[Filter Using Parent Attributes](https://support.profisee.com/wikis/profiseeplatform/filter_using_parent_attributes)

Users cannot change the filter applied in an entity grid control displayed in the browser. It is applied by default as a part of the presentation view and is hidden from users. Users can add additional filters to the entity grid but they cannot alter the hidden filter.
7. Edit the information on the **Sort Columns**. You can use an attribute to sort the grid that will not display as a column in the portal page. You can also re-sort columns in the entity grid control displayed in the browser.

1. Select the columns to use to sort the grid by selecting attributes from the list from the left panel.

In general, it is not effective to use more than three to sort the entity grid. You can use as many attributes as you like to sort the grid, however.

- Click **Select All** to select all of the attributes.
- Click **Clear All** to clear all attribute selections.
- Select individual attributes to add them one at a time.
- Expand a DBA and select one or more attributes beneath it to make a multi-level attribute selection.
2. Select whether to sort each selected attribute using an ascending or descending order by making selections in the Sort Order column.
3. Arrange the sort order by reordering selected attributes in the right panel.

- Move attributes up and down in the list by clicking the up and down arrows.
- Move attributes to the top of list and to the bottom by clicking the paging arrows.
- Remove attributes from the list by selecting the attribute and then clicking **Delete**, or by clearing the selection in the **Available attributes to sort** panel.

You can use an attribute to sort the grid that will not display as a column in the portal page.

Users can re-sort columns in the entity grid control displayed in the browser.

8. Edit the optional settings on the **Options** tab.

1. **Display format**

Select the way the domain-based attribute values display in the entity grid. Possible options include:

- Code [Name]
- Name [Code]
- Name
- Code
2. **Page size**

Define the default number of members that display in the entity grid at once. Users can change the page size in the control on the portal page.
3. **Show validation column**

Select to include the column containing member validation status in the entity grid control.
4. **Use this view as the default view for the entity**

Select to make this presentation view the default configuration for all entity grid controls that include the same entity.

When there is no default presentation view for an entity and no other view is selected, the entity control displays the Name and Code attributes.

A different presentation view can be selected for entities with a default presentation view.

If there is only one presentation view for an entity, then that view is automatically the default.

8. Click **Save and Close**.