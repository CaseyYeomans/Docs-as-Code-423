# Create an Attribute

You can add attributes to an existing entity, or create a new entity and populate it with your own custom attributes. To create an attribute:

1. In the entity grid, right-click any attribute header in the entity where you want the new attribute to appear.
2. Click **Create Attribute** on the menu.

The Attribute Edit dialog appears.
3. In the **Name** field, type the attribute name. This name becomes the attribute header.
4. Do one of the following:

- Select **Free Form** for the attribute type.

1. In the **Display Width** field, specify the default display width of the attribute column (in pixels).
2. Enter the number of decimal places to display in the Decimals field (for the Number data type only)
3. In the **Length** field, specify the maximum number of characters allowed for each value (for Text and Link data types)
4. Select the type of data to display using the **Data Type** menu. You can choose:

- Text
- Number
- DateTime
- Date
- Link

**--or--**

- Select **Domain Based** for the attribute type.

5. In the **Display Width** field, specify the default display width of the attribute column (in pixels).
6. Using the **Domain** menu, select the entity containing the values for this attribute.
5. Select **System Identity for** to make this attribute an identity attribute for a system in the external systems list.

This option is only available for text attributes when an external system is defined in the external systems list.

6. Select **Restricted** to prevent editing of attribute values by users. The Restricted option only allows processes, business rules, API, and other system processes to change or add values for the attribute. Selecting this option essentially makes an attribute read-only to all users.
7. Select **Clear on clone** to clear the value for this attribute when members are cloned.
8. Click **Save**.

The Create Attribute window closes. The new attribute appears at the end of the list of attributes, before the hierarchy columns.