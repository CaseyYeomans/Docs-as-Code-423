# Creating Entities and Attributes in Profisee Portal

To create a new entity in Profisee Portal:

1. Navigate to the **Entities** tab in the **Administration** section of Profisee Portal.
2. Click the **+** icon to add a new entity.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-if94a29b08e2cad81.png)
3. Enter a Name and Description for the new entity, then click **Continue**.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id95055241598f43f.png)
4. Optionally, enter the FontAwesome Classname id to create an icon to be displayed with the entity.
5. Optionally, select the **Create Code values automatically** option to automatically create code values for records in this entity.
6. Optionally, include a File Attachment by clicking the + icon under **File Attachments**and including the Type and Allowed File extensions. For more information, see [File Attachments](https://support.profisee.com/wikis/profiseeplatform/add_a_file_attachment).
7. Optionally, select a Data Product to include this entity within. For more information, see [Data Products](https://support.profisee.com/wikis/profiseeplatform/Data_Products_Overview).
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-icd767362150e456c.png)
8. Click **Save and Close** to finalize and create the entity without attributes, or **Save** if you wish to add attributes to the entity. You cannot add attributes until the entity has been saved.

### Adding Attributes to the Entity

1. fWith an entity open, navigate to the Attributes tab.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibf06da9a435f7648.png)
2. Click the **+** icon on the attribute grid to create a new attribute.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ib794792452ba351b.png)
3. Enter a name and description for the new attribute under the **Name** and **Description** fields.
4. Select the **Type** of the attribute. The attribute type determines the rest of the settings for the attribute.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i95fbc5f3d54319b2.png)

A **Free Form Attribute**that has entirely user-defined values.
A **Domain-Based Attribute (DBA)** is an attribute with values that are populated by records from another entity.

**For a Free Form Attribute**

Select Restricted to prevent editing of attribute values by users.The Restricted option only allows processes, business rules, API, and other system processes to change or add values for the attribute. Selecting this option essentially makes an attribute read-only to all users.

1. Set the Display Width in pixels.
2. Select a Data Type from the dropdown list (Text, Number, DateTime, Date, or Link).
3. Set the maximum length (in characters) for this attribute.
4. Select **Clear on clone** to clear the value for this attribute when members are cloned.
5. Click **Save**. The Create Attribute window closes.

**For a Domain-Based Attribute**

1. Set the Display Width in pixels.
2. Select the Domain for this attribute. The Domain is the entity containing the referenced values for this attribute.