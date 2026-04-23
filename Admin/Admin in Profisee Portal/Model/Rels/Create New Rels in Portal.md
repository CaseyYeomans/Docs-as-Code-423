# Creating New Relationships in Portal

To create a new Relationship in Profisee Portal, click the **+** icon on the top-right corner of the toolbar, then select which relationship type you would like to create.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i6dd908ab4b257f05.png)

## Creating a One to Many Relationship

A **One to Many** relationship allows one parent entity to relate to multiple records in a child entity via a Domain-Based Attribute. These kinds of relationships are useful for defining a relationship where one record in an entity contains multiple related child records. For example; an entity called "Product Category" would likely contain several related "Product" records.

After selecting this relationship type:

1. Select the **Child Entity (many)** to be used in this relationship. This should be the entity with multiple related records.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibb084264fd8aadb2.png)
2. Select the **DBA Link**. This is a Domain-based Attribute that is shared between the two entities. The selected DBA is used as the **Parent (one)** entity.
3. Click **Continue**. The Relationship Form opens and autopopulates information about the entities and their relationship.
4. Review and optionally edit the information in the Relationship Form, then select **Save** or **Save and Close** when finished.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iedaf89aa3cc0a417.png)

## Creating a Recursive Relationship

A **Recursive Relationship**is a type of relationship where the Parent and Child records are contained within the same entity. Recursive Relationships can be used to define relationships where an entity is related to itself via a Domain Based Attribute (DBA) relationship. For example; an Employee entity might have a Manager DBA relationship with the Employee entity as the domain. This means the domain for the list of managers will be the list of records in the Employee entity.

After selecting this relationship type:

1. Select the entity to be used for the recursive relationship.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i33b6776a50248efd.png)
2. Select the DBA Link to be used for this relationship. This is a Domain-based attribute within the entity that references another instance of that same entity -- effectively creating a hierarchy or dependency within itself.
3. Click **Continue**. The Relationship Form opens and autopopulates information about the entities and their relationship.
4. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i66024e9162863762.png)Review and optionally edit the information in the Relationship Form, then select **Save** or **Save and Close** when finished.

## Creating a Many to Many Relationship

A **Many to Many Relationship**is a type of relationship between two entities that is established by a Bridge Entity. This bridge entity links the parent entities using two Domain-based Attributes (DBA) to define the related entities. A valid bridge entity must have two Domain-based Attributes that correspond to the domains of the two parent entities.

Example: To demonstrate a relationship between **HmProduct** and **HmVendor**, the entity **HmProductVendor**--which contains the Product and Vendor domains--is used as a bridge entity to define the relationship between them.

This relationship can be further defined by the use of Bridge Properties, which are derived from the other attributes within the bridge entity. These attributes can be selected to display additional information within the relationship list. In the example above, a data steward would be able to manually define an End Date for the relationship in DateTime format, as well as any Notes about the relationship in plain text form.

After selecting this relationship type:

1. Select an entity for **Entity A** and **Entity B**. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i90bfb65a682092c2.png)
2. Click **Next.** The Bridge Entity dialogue opens and autopopulates**.** Here, the bridge entity is atuomatically created as part of the relationship definition.
3. Click **Continue**. The Relationship Form opens and autopopulates information about the entities and their relationship.
4. Review and optionally edit the information in the Relationship Form.
5. If desired, add or edit Bridge Attributes for this relationship.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i200f1e03a5b15eaa.png)

- Select the **Show** checkbox to cause the attribute to show in the bridge table record creation dialogue.
- Click the **+** icon to create a new attribute to be used as a Bridge Attribute. See **Adding a new Attribute to a Many-to-Many Relationship** below for more information.

7. Click **Save** or S**ave and Close** to create the relationship.

### Adding a new Attribute to a Many-to-Many Relationship

1. Click the **+** icon on the Bridge Attribute pane to create a new attribute.
2. Enter a name and description for the new attribute under the **Name** and **Description** fields.
3. Select the **Type** of the attribute. The attribute type determines the rest of the settings for the attribute.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i95fbc5f3d54319b2.png)

A **Free Form Attribute**that has entirely user-defined values.
A **Domain-Based Attribute (DBA)** is an attribute with values that are populated by records from another entity.

**For a Free Form Attribute**

Select Restricted to prevent editing of attribute values by users.The Restricted option only allows processes, business rules, API, and other system processes to change or add values for the attribute. Selecting this option essentially makes an attribute read-only to all users.

1. Set the Display Width in pixels.
2. Select a Data Type from the dropdown list (Text, Number, DateTime, Date, or Link).
3. Set the maximum length (in characters) for this attribute.
4. Select **Clear on clone** to clear the value for this attribute when records are cloned.
5. Click **Save**. The Create Attribute window closes.

**For a Domain-Based Attribute**

1. Set the Display Width in pixels.
2. Select the Domain for this attribute. The Domain is the entity containing the referenced values for this attribute.