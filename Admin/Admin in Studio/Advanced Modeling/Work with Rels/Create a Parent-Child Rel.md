# Create a Parent-Child Relationship

A **Parent-Child Relationship**is a type of relationship where one member in a Parent entity relates to one or more members in a Child entity via a Domain Based Attribute relationship. Parent-child relationships are useful for defining a relationship where one member in an entity contains multiple related child members. For example, an entity called "Product Category" would likely contain several related "Product" members as children.

To model a new Parent-Child Relationship:

1. Navigate to the **Advanced Modeling** administration tab.
2. Expand the entity for which you want to create a relationship.
3. Right click **Relationships** beneath the entity, then hover over **Create**.
4. Select **Parent Relationship** or **Child Relationship**.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ib1e621230ed82fb1.png)

Selecting **Child Relationship** will automatically designate the selected entity as the Parent entity. Selecting **Parent Relationship** will designate the selected entity as the Child entity.
5. Select the **Entity and Attribute** for the child entity.
6. Define the **Predicate**, **Role**, and **Role Plural** for the child entity.

The **Predicate** is a user-defined specification of how an entity is related to the other entity.

The **Role** is the singular version of how this entity should be named. This should typically be the same as the entity name. For instance, if your entity is named **Account,**the Role name would be **Account**, and the **Role plural** would be named **Accounts.**

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i86f18f7c359de6d6.png)

7. Click the Parent relationship card, then define the **Predicate** and **Role** for that entity.
8. Click **Save** to save and create the relationship.