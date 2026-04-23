# Link Controls

Filter and entity grid controls can be linked to other controls. Controls are linked using the **Link to** option on a selected control.

## Send and Receive Controls

When two controls are linked, there is always a **sending control** and a **receiving control**. The sending control provides configuration information for a sending attribute, while an attribute in the receiving control receives this configuration.

For example, you can configure a filter control to use the Color domain attribute. The filter control sends the filter values--the attribute, Color, and associated options like display and input interface--to the receiving control, linking the appropriate entity in the receiving zone (in this example, Product).

After the Product entity is linked, configure a receiving attribute in the Links panel. Only valid attributes will appear in the list. When a receiving attribute is selected, it receives the filter information and applies the filter control to the selected Color attribute in the entity grid.

Controls must be first [added to a zone in a portal application page](https://support.profisee.com/wikis/profiseeplatform/configure_fastapps_portal_page_controls) before they can be linked.

## See Also

[Link Entity Grid Controls](https://support.profisee.com/wikis/profiseeplatform/link_entity_grid_controls)

[Link Filter Controls](https://support.profisee.com/wikis/profiseeplatform/link_filter_control)