# Manage Field Relationships

The Managing Field Relationships dialog lets you create many-to-many relationships between field controls in a form for related DBA attributes.

To create relationships between form fields, you must have at least one bridge table (entity) linking the attributes involved. This bridging entity must include the relationships that you want to use with the entity in your form.You can only include attributes in your form that are available in the model context, so the bridge table must also include the attributes in the form that you want to use in the relationship.

The bridge table will let you limit the options presented to end users in forms through the use of parent, child, or sibling relationships between attributes.

Attributes at the same level in a model are called siblings. Selecting the bridge table and the attribute to use as a sibling lets you use fields in the form to create parent and child relationships that the one of the siblings does not have a direct relationship with. Using the sibling relationship, the selected attribute can access parent and child relationships through the sibling.

Use field relationships in conjunction with parent fields to create forms that are easier for workflow participants to use. For an example of creating a sibling relationship, see [Creating a Sibling Relationship Between Form Attributes](https://support.profisee.com/wikis/profiseeplatform/create_sibling_relationships_between_form_attributes). The sibling relationship is commonly used in form creation to limit the user's menu selections to valid combinations.

To create a relationship between fields in a form:

1. [Edit](https://support.profisee.com/wikis/profiseeplatform/edit_form) an existing form, or [create a new form](https://support.profisee.com/wikis/profiseeplatform/create_a_new_form).
2. Right-click **Layout**.
3. Click **Add field** on the menu.
4. In the properties for the field control, click inside the **Attribute** row.
5. Click the down arrow in the row to open the list.
6. Select a DBA from the list of attributes.

Only DBAs include the ability to manage field relationships.

7. Right-click the field control in the layout.
8. Click **Manage field relationships** on the menu.

The Manage Field Relationships dialog appears.
9. Click the **Siblings** tab.
10. In the center of the tab, click **Create Sibling Relationship**.

The **Create Bridge Table Relationship** dialog appears.
11. From the **Entity** list, select the entity containing the attribute to form a sibling relationship with.

If there are no appropriate bridge tables to use (that is, no entities containing a sibling for the selected attribute), then the list is empty. There can also be multiple entities containing sibling attributes.

12. From the **Bridge Attribute** list, select the attribute which will act as a bridge between the attributes.
13. Click **OK**.

The sibling attributes display on the Siblings tab. These are the attributes with field controls in the form that the selected attribute has a sibling relationship with.
14. Create sibling relationships with the field controls for the listed siblings by selecting the attributes from the Available Fields column and using the arrow button to move them into the Related Fields column.

When participants view the form, the fields will display the values for the initiating member based on the sibling relationship.
15. Click the **Parents** tab.
16. Create parent relationships between the selected field control and the parent attribute candidates in the form by selecting the attributes from the Available Fields column and using the arrow button to move them into the Related Fields column.

When participants view the form, the fields will display the values for the initiating member based on the parent relationship.
17. Click the **Children** tab.
18. Create child relationships between the selected field control and the child attribute candidates in the form by selecting the attributes from the Available Fields column and using the arrow button to move them into the Related Fields column.

When participants view the form, the fields will display the values for the initiating member based on the child relationship.
19. Click **OK** to save your changes.

If multiple children share a parent, all instances of that parent must have the same value. The form will not display data properly if multiple instances of a parent have different values.