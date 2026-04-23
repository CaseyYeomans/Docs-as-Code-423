# Create and Edit Attributes in the Portal

Profisee Administrators can create new attributes in the Profisee Portal from any entity grid. Attributes created in the portal are persisted into Profisee FastApp Studio and function identically to attributes created in FastApp Studio.

1. Navigate to an entity in Profisee Portal and click the **vertical ellipsis**icon in the top-right corner of the entity grid and select **Create Attribute** from the menu. The **Create [Entity Name] Attribute** panel opens.
2. Enter a name and description for the new attribute under the **Name** and **Description** fields.
3. Select the **Type** of the attribute. The attribute type determines the rest of the settings for the attribute.

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

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i1957cedaafebc532.png)

## Edit an Attribute

You can edit an attribute and change any of the above settings by right-clicking the **Attribute** column header and selecting **Edit Attribute**. From here, you can change any of the above properties.