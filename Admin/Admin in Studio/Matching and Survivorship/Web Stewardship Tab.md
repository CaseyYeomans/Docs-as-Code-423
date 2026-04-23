# Web Stewardship Tab

The Web Stewardship tab defines the matching and survivorship options available to data stewards using the Maestro Portal. Additional configuration is required--to perform matching and survivorship through Portal, you must also have a portal application with a portal page or form containing an appropriately configured match cluster control, as well as the proper rights to access the related data. For more information, see [Assign Permissions for Matching Tasks](https://support.profisee.com/wikis/profiseeplatform/assign_permissions_for_matching_tasks).

## Options Tab

The Options tab lets you control access to the various matching and survivorship stewardship functions users can perform through the portal. If an action is not selected, then no user will be able to perform that action, regardless of permissions. If no actions are selected, the match cluster control operates in read-only mode.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i365867834f43533c.png)

### Configurable Options

Click the appropriate checkbox to enable each of the following options:

- Approve or reject a record in the cluster
- Apply survivorship to the cluster
- Allow manual promotion to Golden Record

- Allow Promote All
- Allow manual harmonization to source records

- Allow Harmonize All
- Allow Merge
- View match details for a record

Select an appropriate option from the dropdown lists for the following options:

- Orphaned golden record behavior (Retain or Delete)

An orphaned record is a golden record that has no children records in the match cluster. This situation can occur if a steward reviews matching results and manually splits or combines records from at least two match clusters where a golden record is left alone without any other records in its match cluster.

It can also occur if a golden record's match cluster records are deleted from the source systems and are removed from the data set. If the above **Orphaned golden record behavior** setting is set to Delete, Profisee automatically deletes orphaned golden records.

- Stewardship View (Select a Presentation View)

The presentation view displays unrestricted attributes for this entity under the Survivorship section of the portal. Attributes displayed here can be used to change the values on match records if Promotion and Harmonization are enabled.

Control attributes should not be manually set using Promotion or Harmonization; they should be Restricted as not to be displayed in the presentation view.

- Open/Edit Form (Select a Form)

## Lookup-before-create Tab

The Lookup-before-create tab allows you to configure the behavior and appearance of LuBC if it is enabled on a portal page's entity grid control. To do so, create a presentation view to display the desired attributes that are returned for LuBC. It is recommended to use Name, Code (if meaningful), attributes used for matching, and any additional attributes that might aid in determining if the record is a match to the record being created. Additionally, when viewed in the portal, a **Similarity**column is added to as the first column in this presentation view automatically. Results are displayed in descending order of Similarity.

Once you have configured a presentation view for your LuBC:

1. Select the presentation view you want to use to display LuBC results under the **Results view** dropdown list.
2. Select the order of the attributes to be displayed during LuBC results.
3. Enter a column label for each attribute to be displayed during LuBC results.

If no presentation view is selected, the LuBC results will be displayed with the columns: **Code**, **Name**, **[Matching Attributes]**.

###

### Configurable Options

- Include golden records in search results by clicking the checkbox. The default setting is to exclude golden records.
- Change the display order of attributes:
- Select the attribute you wish to move.
- Use the arrow icons to move it up or down in the list.
- Attributes cannot be removed from the list, but they can be renamed. To customize attribute labels:
- Double-click in the Attribute Label field to make it editable.
- Edit or change the label.

To complete configuration for use in the web, you must also configure settings on the entity grid in the associated Portal application. Refer to [Configure The Entity Grid Control.](https://support.profisee.com/wikis/profiseeplatform/configure_the_entity_grid_control)

## Merge Tab

The Merge tab provides controls for configuring settings and control attributes to enable external system merge operations.

###

### Configurable Options

- Select a merge parent, or create a new one
- Select an external system as the basis for a new merge status attribute
- Create a new merge status attribute, or select an existing one to associate with the new external system

## Other Dependencies

- The match cluster must have a golden record in order to perform manual survivorship.
- The strategy must include Matching, to allow users to view match details for a record.
- The strategy must include Survivorship, to allow users to run survivorship on the cluster.
- The entity must include system-aware identity management (SAIM) attributes to allow users to perform external system merge functions.

It is not possible to configure Merge settings when SAIM attributes are unavailable in the entity. See [System Aware Identity Management (SAIM)](https://support.profisee.com/wikis/profiseeplatform/system_aware_identity_management_overview) for information on configuring SAIM.