# Create System Identity Attributes Using Adaptive Modeling

After you have added systems to the external systems list (see [Edit the External Systems List](https://support.profisee.com/wikis/profiseeplatform/edit_the_external_systems_list)), the next step is to create attributes to use to store the unique identifiers in other systems. In this way, external systems can always identify members, even if they are unable to use the Profisee code due to proprietary ID formats.

To add a system-aware identity attribute with adaptive modeling:

1. In a new Workspace tab, open the entity that will contain the system-aware identity attribute.
2. Right-click an existing attribute and then click **Create Attribute** on the menu.

The Create Attribute dialog appears.
3. Type the name of the new attribute in the **Name** field.
4. Select **Free Form** for the attribute type.
5. Make any selections for **Display width** and **Length** settings.
6. From the **Data Type** list, select **Text**.

**NOTE**: The only allowed data type for system identity attributes is the free-form text attribute type.
7. Select the **System Identity** for option.
8. From the list, select the system to use with this attribute.

Restricted and Clear on clone are automatically selected for system identity attributes. While you can change the Restricted setting, you cannot change the Clear on clone setting. System-aware identity attributes must have Clear on clone enabled to avoid creating duplicate members on external systems.

All data members that are evaluated by a data transfer strategy with system aware identification enabled must have values for the system identity attribute. It is sometimes prudent to disable the Restricted setting on system identity attributes so that it is possible to modify system identity attribute values when adding new members.

9. Click **Save**.

System identity attributes can similarly be created by editing existing free-form text attributes and selecting the System Identity for option.