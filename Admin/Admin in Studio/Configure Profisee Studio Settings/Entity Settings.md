# Entity Settings

The following settings are available in the **Entity Settings** tab of Desktop Settings.

### Default Data Import Behavior

| Option | Function |
| --- | --- |
| Preview records before publishing | Enables a preview in the grid before publishing using the Profisee data import process. The preview gives you the opportunity to review data before it is published. |
| Automatically add domain values | When unrecognized values in an attribute column are mapped to an existing domain-based attribute, Profisee automatically adds the values as new domain members. When this option is not selected, then new imported DBA values are discarded. This setting applies only to imported data. This setting is only relevant when the Preview Records... setting is off, as the Publishing setting governs this behavior when previewing data in the entity grid. |

###

###

###

###

###

###

### Domain Attributes

| Option | Function |
| --- | --- |
| Edit mode | Enables Popup or AutoComplete for domain-based attribute value selections when the source domain member count is above the List Limit setting. The Popup option opens a pop-up window containing all possible domain members for searching and filtering, while AutoComplete attempts to complete the code value of the referenced member as you type. Auto Complete only works with member codes, so your DBA display type must be "Code" or "Code [Name]". |
| Always check for changes | Enables automatic checks for changes in the reference entity for new domain members so that they appear in the list of choices as they are added. |
| List Limit | The maximum number of source domain members to display in a drop-down list. Above this limit, the selected Edit Mode alternative will be used. |

###

###

###

###

###

###

###

###

### Publishing

| Option | Function |
| --- | --- |
| Use deferred publishing mode for entity grid edits | Changes to data are highlighted in the data grid, but are not applied to the central repository until you click Publish. When this option is cleared, changes publish immediately as your cursor leaves an edited cell. |
| Publish batch size | Determines the batch size, in number of members, that Profisee uses to publish changes. Changing this setting is generally unnecessary. (default = 1000) |
| Automatically add domain values | For any unrecognized values pasted into a domain-based attribute column being mapped to an existing domain-based attribute, automatically add the new values as domain members. When this option is not selected, then new values are rejected as errors. This setting applies only to data edits made in the entity grid. |
| Immediately run data quality rules on grid members after grid editing | Runs data quality rules automatically after every edit, and before refreshing data from the server. Selecting this option can help to ensure all of the data entered is valid. But it's usually not necessary, given the normal speed of background rule processing, and it slows down the responsiveness of Profisee as data is entered. |

###

###

###

###

###

###

###

###

###

### Default data export behavior

| Option | Function |
| --- | --- |
| Batch size | The default number of rows in a single batch when exporting member data. (default = 1000) |