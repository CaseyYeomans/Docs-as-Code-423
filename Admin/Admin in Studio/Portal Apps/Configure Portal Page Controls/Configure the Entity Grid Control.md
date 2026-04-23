# Configure the Entity Grid Control

The Entity Grid control lets you insert an entity grid into a portal application page. The first column displayed in an entity grid provides a clickable link to the form associated with the grid. To work as clickable link to the form, the first column should not be a match group column and should not be a link attribute type.

To configure the Entity Grid control:

1. Follow the instructions to [create a portal application page](https://support.profisee.com/wikis/profiseeplatform/add_a_new_portal_application_page), adding an Entity Grid control.
2. Under Properties, enter a name for the control in the **Name** field.

The Name field is for administrative reference only and does not display to users when the control is viewed in the portal.

3. From the **Entity** list, select the entity to use in the control.
4. From the **View** list, select the presentation view to use with the control.

Views define the columns that display in the entity grid, the filters that are applied, and column sorting options. Views are created using the Presentation Views feature. For more information, see [Create a new presentation view](https://support.profisee.com/wikis/profiseeplatform/create_a_new_presentation_view).

If you do not select a presentation view, then the entity's Name and Code columns will display by default.

5. From the **Add member form** list, select the form that displays to portal users when they add members to the displayed entity.

The Add member form is the form which displays when a user adds a new member using this entity grid control. Forms are developed using the [Forms](https://support.profisee.com/wikis/profiseeplatform/forms_overview) feature.

User permissions will determine whether a specific user can add data.

If no Add member form is included, then users will not be able to add new members to the entity.

7. From the **Open member form** list, select the form that will display to portal users when they open members displayed in the entity to update them.

The Open member form is the form which displays when a user views and edits member data using the entity grid control. Forms are developed using the Forms feature.

User permissions will determine whether a specific user can edit data.

If no Open member form is included, then users will not be able to open and update members.

After the entity grid is configured, you can include it as is, or link it to another entity grid, or link a filter control to it.

8. Select **Can delete** to make it possible for users to delete information from the selected entity using this control in the portal page.

User permissions will determine whether a specific user can delete data. When the Can delete option is unselected, then no users can delete information using the control, even if user permissions allow it.

9. Select the matching strategy the entity grid conforms to under the **Matching strategy** dropdown.
10. Check **Enable hyperlink to raise match group control** if desired. This feature allows users to navigate to match group control by directly clicking the match group within the entity grid. This setting is recommended.
11. Check **Enable lookup-before-create** if desired. This feature applies [lookup-before-create](https://support.profisee.com/wikis/profiseeplatform/lookup_before_create) to the matching strategy

If checked, additionally check **Prohibit** **add if lookup-before-create fails** if desired. If lookup-before-create fails when attempting to add a new member, no member will be added.