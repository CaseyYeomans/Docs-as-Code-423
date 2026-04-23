# Create System Identity Attributes Using Advanced Modeling

After you have added systems to the external systems list (see [Edit the External Systems List](https://support.profisee.com/wikis/profiseeplatform/edit_the_external_systems_list)), the next step is to create attributes to use to store the unique identifiers for other systems. In this way, external systems can always identify members, even if they are unable to use the Profisee code due to proprietary ID formats.

To add a system-aware identity attribute with advanced modeling:

**--or--**

The **Create Attribute** dialog appears.

1. In Advanced Modeling, open the model with the entity that will contain the system-aware identity attribute.
2. In the model tree, expand the entity where you want the new attribute to appear.
3. Do one of the following:

1. In the model tree, right-click **Attributes**.
2. Click **Create** on the menu.
3. In the model tree, select **Attributes**.
4. Click **Add** on the modeling grid toolbar.
4. Type the name of the new attribute in the **Name** field.
5. Select **Free Form** for the attribute type.
6. Make any selections for **Display width** and **Length** settings.
7. From the **Data Type** list, select **Text**.

The only allowed data type for system identity attributes is the free-form text attribute type.

8. Select the **System Identity for** option.
9. From the list, select the system to use with this attribute.

- **Restricted** and **Clear on clone** are automatically selected for system identity attributes. While you can change the **Restricted** setting, you cannot change the **Clear on clone** setting. System-aware identity attributes must have Clear on clone enabled to avoid creating duplicate members on external systems.
- All data members that are evaluated by a data transfer strategy with system aware identification enabled must have values for the system identity attribute. It is sometimes prudent to disable the Restricted setting on system identity attributes so that it is possible to modify system identity attribute values when adding new members.
10. Click **Save**.

The attribute is created.