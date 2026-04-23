# Create a Recursive Relationship

A **Recursive Relationship**is a type of relationship where the Parent and Child members are contained within the same entity. Recursive Relationships can be used to define relationships where an entity is related to itself via a Domain Based Attribute (DBA) relationship. For example, an Employee entity might have a Manager DBA relationship with the Employee entity as the domain. This means the domain for the list of managers will be the list of members in the Employee entity.

To model a new Recursive Relationship:

1. Navigate to the **Advanced Modeling** administration tab.
2. Expand the entity for which you want to create a relationship.
3. Right click **Relationships** beneath the entity, then hover over **Create**.
4. Select **Recursive Relationship**.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-if93f86cf0ea239ff.png)

5. Select the attribute for the child entity.
6. Define the **Predicate**, **Role**, and **Role Plural** for the child entity.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i4f91acc46bcf6a3f.png)

The **Predicate** is a user-defined specification of how an entity is related to the other entity.

The **Role** is the singular version of how this entity should be named. This should typically be the same as the entity name. For instance, if your entity is named **Account,**the Role name would be **Account**, and the **Role plural** would be named **Accounts.**

7. Select the Parent entity card and define the **Predicate** and **Role** for the parent entity.
8. Click **Save** to save and create the relationship.