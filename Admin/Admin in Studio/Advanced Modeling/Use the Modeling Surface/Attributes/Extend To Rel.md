# Extend  To Relationship

Relationships are based on DBAs. You can extend to a relationship from any DBA--Parent/Child or Recursive--not already referenced by an existing relationship.

To extend a DBA to a Parent/Child relationship:

1. Navigate to **Administration | Advanced Modeling**.
2. Open the desired model (**Open the model from the server** or **Open a model file**).
3. In tree view, select the entity containing the desired attribute. In the example pictured below, we select the Product entity.
4. Expand the list of attributes and select one you wish to extend. We select Color.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i57a3d85561693614.png)
5. Right-click and select **Extend to Relationship**, as shown in the image below. The Relationship Designer window opens.
6. The Parent and Child role cards are auto-populated based on the DBA settings, which define the details of the relationship. The parent and child entities and the attribute name are read-only, and cannot be changed.
7. Click **Save**. The new relationship appears in the modeling tree.
8. Click **Publish to Server**.