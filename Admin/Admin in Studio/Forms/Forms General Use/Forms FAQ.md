# Forms FAQ

The following are answers to frequently asked questions about Forms:

- I set a value for a parent attribute that is part of a parent-child relationship on my form and saved it, but the selection for the parent attribute is not persisting after the save. Why?

Parent values are only included to allow for the navigation and selection of child attribute values. When selecting fields in a parent-child relationship, you can only save selections for the child attribute.

- I have attributes on my form that are in a parent-child relationship. How can I view the parent attribute's value in my presentation view?

If you want a parent value to be displayed in a presentation view, use the presentation view's multi-level attribute capabilities.

If you created a new attribute on a child entity with the same name as a parent entity, you may have added the wrong attribute to your presentation view. You should *not* create a new attribute with the same name as a parent entity to display that attribute on a presentation view.

- I have a match cluster control on my form. Why is the hyperlink for my form in the portal not active?

If you have unsaved changes on the form, the hyperlink will not become active until the changes have been saved.