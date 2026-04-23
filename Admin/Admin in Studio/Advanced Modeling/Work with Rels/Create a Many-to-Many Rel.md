# Create a Many-to-Many Relationship

A **Many to Many Relationship**is a type of relationship between two entities that is established by a Bridge Entity. This bridge entity links the parent entities using two Domain-based Attributes (DBA) to define the related entities. A valid bridge entity must have two Domain-based Attributes that correspond to the domains of the two parent entities.

In this example: To demonstrate a relationship between **HmProduct** and **HmVendor**, the entity **HmProductVendor**--which contains the Product and Vendor domains--is used as a bridge entity to define the relationship between them. ![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i730af289cee0c75.png)

This relationship can be further defined by the use of Bridge Properties, which are derived from the other attributes within the bridge entity. These attributes can be selected to display additional information within the relationship list. In the example above, a data steward would be able to manually define an End Date for the relationship in DateTime format, as well as any Notes about the relationship in plain text form.

To model a new Many to Many Relationship:

1. Navigate to the **Advanced Modeling** administration tab.
2. Expand one of the entities for which you want to create a relationship.
3. Right click **Relationships** beneath the entity, then hover over **Create**.
4. Select **Many to Many Relationship** from the list.![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i6534ba7c4cd58d6a.png)
5. Specify the **Predicate**, **Role**, and **Role plural** for the first entity.

The **Predicate** is a user-defined specification of how an entity is related to the other entity.

The **Role** is the singular version of how this entity should be named. This should typically be the same as the entity name. For instance, if your entity is named **Account,**the Role name would be **Account**, and the **Role plural** would be named **Accounts.**

6. Click **Entity 2** on the relationship model.
7. Click the **Entity** dropdown within the **Entity 2 details** panel and select the second entity for which you want to create a relationship.
8. Specify the **Predicate**, **Role**, and **Role plural** for the second entity.![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i49fbe48c0175230d.png)
9. Click **Bridge Entity**on the relationship model.
10. Specify a name for the relationship. By default, the relationship is named **[Entity 1]<->[Entity 2]**.
11. Select an entity from the dropdown list to become the bridge entity.

For an entity to be used as a Bridge Entity, it must have the **Create code values automatically** setting enabled using data modeling, and it must have at least one attribute whose domain is Entity 1 and at least one attribute whose domain is Entity 2.

12. Select a link for Entity 1 and Entity 2. These links are DBAs whose domains correspond to Entity 1 and Entity 2.
13. Optionally select Bridge properties to be displayed when viewing the relationship on a form.
14. Click **Save**.

Once saved, you can edit or delete this relationship by right-clicking it within the list in the Advanced Modeling tab and selecting **Edit** or **Delete**.![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i2b087a987944d346.png)

Note that when creating a form to display this relationship in a relationship list, you must use the entity specified in **Entity 1** or **Entity 2** as the parent entity.