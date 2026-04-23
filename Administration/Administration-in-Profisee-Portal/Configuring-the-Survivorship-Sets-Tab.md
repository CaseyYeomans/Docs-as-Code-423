# Configuring the Survivorship Sets Tab

Survivorship sets contain all attributes related to each other to represent a piece of data that will be promoted to the golden record from a single source record.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id36ee352cb177a44.png)

Multiple sets are used to separate different pieces of data, or when different promotion criteria are needed.

• More sets will take longer to process, so only add attributes required to be in the Golden record like Name, Email, Phone, Address, Etc.

 • Source System ID, Source Updated Date, etc. should not be used as they pertain to the source record only.

 • Address Verification Status, Match Status, etc. are not Golden record data but only qualify the source record.

Click the **+**icon on the Survivorship Sets table to create a new survivorship set. The Survivorship Attribute Sets panel opens.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i83be9b12fdd96265.png)

1. Enter a **Name** for the survivorship attribute set. The default name is Set 1.
2. Select one of the following from the **Promotion Behavior** list. This specifies when the golden records should be updated.  Each survivorship attribute set must have at least one harmonization or promotion action policy or you will not be able to save the strategy.
   * **None**—Golden records will not be updated. Use this option if you only want to harmonize source records with this attribute set, or if you want to temporarily disable promotion for the selected attribute set.
   * **Only copy if the attribute is blank**—Populate golden records from the source records only if the golden record attribute value is blank. All blank values will be set, and the populated values will not be overwritten.
   * **Only copy if all attributes are blank**—Populate golden records from the source records only if all attribute values in this set are blank in the golden record.
   * **Always copy (overwrite)**—Always update the golden record attributes regardless of the golden record attribute values.
3. If desired, create a filter to determine **Promotion Conditions**using the expression editor.
4. Select an option for **Harmonization Behavior** (see behavior options above).
5. If desired, create a filter to determine **Harmonization Conditions**using the expression editor.

You can choose behavior for Promotion, Harmonization, or both. At least one behavior must be selected.

6. Select one or more attributes from the **Available Attributes** list and add them to the **Selected Attributes** list, either by double-clicking the attribute name or by clicking the arrows to move selected attributes between the panes.

You can create additional attributes sets as needed by repeating the above steps. You can keep the default set names, or customize the names to help you rerecord what actions they perform. You can select the sets from the list to edit or delete them. You can use the same attribute across multiple attribute sets.  
  
If the Apply Nulls checkbox is selected, the attribute will be copied into the golden record regardless of value. If it is not selected, blank attributes will not be copied into the golden record.   
  
When the appropriate harmonization and promotion options are enabled, all existing attribute sets are processed when the corresponding strategy is processed.

---