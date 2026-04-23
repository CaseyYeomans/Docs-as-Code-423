# Link Filter Controls

[Filter controls](https://support.profisee.com/wikis/profiseeplatform/cofigure_the_filter_control) can be linked to entity grids or to other filter controls in other zones on the same portal application page. Linking a filter control to an entity grid provides portal users with a filter that they can apply to the linked entity grid.

To link a filter control:

1. In the Portal Page Configuration dialog, in the zone where it is configured, right-click the filter control.

A menu opens.
2. In the menu, click **Link to**.

For DBA filters:

A list appears, displaying the potential receiving controls for the link. For a control to appear in the list of candidates to link to, the sending attribute in the first entity must be a domain entity for an attribute in the receiving control.

For FFA filters:

A list of entity grid and filter controls display, containing:

- Free-form attributes of the type in the sending control
- Domain-based attributes where the domain includes free-form attributes of the type in the sending control
3. Select the control to link to.

The connection appears In the **Links** panel.
4. In the **Receiving Attribute** column in the **Links** panel, select the attribute to receive the sending attribute in the control. This is the attribute that will be constrained by the filter selection.

If only one applicable receiving attribute exists the receiving control, it is automatically selected.

For DBA filters:

The attributes which display in the list are only the attributes that are candidates to be receiving attributes. That is, only the attributes with the sending attribute as a domain qualify as receiving attributes. You cannot link unrelated attributes.

For FFA filters:

A list of all attributes relevant to the filter displays, depending on the selected input mode:

- Text input mode: all attributes compatible with text filters display (text, link, DBA, file)

For file attributes, only the name of the file is searchable. The file contents are not.
- Numeric input mode: free-form number attributes display
- Date picker input mode: Date free-form attributes display

Include time: Select to include an editable time control with the date picker. Use this option for DateTime attributes that include time.

An unlinked filter control will display in a portal application page, but it does not perform any useful function.

The attribute information defined in a filter control (the sending attribute) is sent to the receiving attribute of another filter control or an entity grid control.

Linking a filter to an entity grid displays a filter in the portal with the defined filter.

Linking a filter to another filter constrains the available options in the receiving filter based on the selection in the sending filter. The second filter can then link to an entity grid, or even another filter.

To set up a filter so that it filters an entity, create the link from the filter and link it to the entity.