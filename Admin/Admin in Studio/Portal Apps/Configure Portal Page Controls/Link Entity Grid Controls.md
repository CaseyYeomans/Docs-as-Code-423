# Link Entity Grid Controls

After you have added an [entity grid control](https://support.profisee.com/wikis/profiseeplatform/configure_the_entity_grid_control) to a zone in a portal application page, you can use the **Link to** option to link it to an entity grid in another zone on a portal application page.

For general information on linking controls, see [Linking Controls](https://support.profisee.com/wikis/profiseeplatform/link_controls).

To link an entity grid control:

1. In the Portal Page Configuration dialog, in the zone where it is configured, right-click the entity grid control.

A menu opens.
2. In the menu, click **Link to**.
3. Select the entity grid control to link to.

The connection appears In the **Links** panel.
4. In the **Receiving Attribute** column, select the attribute that will receive the sending attribute in the control.

If only one applicable receiving attribute exists the receiving control, it is automatically selected.

Linking one entity grid to a second entity grid sends the selection in the first entity to the second one. The sending control will drive the selections displayed in the receiving control.

One entity grid control can have multiple inbound (from sending attributes in other entity controls) and outbound (from receiving attributes to other entity controls) connections.

You will normally link two entity grids together when you want the selection in one grid to determine the data displayed in the second grid. For example, configuring a Color domain attribute in one entity grid and linking it to a Product entity grid (where Color is a domain for a DBA) causes only the members with the color selected in the first grid to display in the second grid.