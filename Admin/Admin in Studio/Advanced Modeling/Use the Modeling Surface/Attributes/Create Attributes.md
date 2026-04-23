# Create Attributes

You can edit an attribute within an entity from the Advanced Modeling tree view.

1. Expand **Entities** container within the model.
2. Expand the entity containing the attribute you want to edit.
3. Do one of the following:

1. In the model tree, expand **Attributes**.
2. In the model tree, right-click the attribute you want to edit.
3. Click **Edit** on the menu.

**-or-**

1. In the model tree, select **Attributes**.
2. In the modeling grid, select the attribute that you want to edit.
3. Click **Edit** on the modeling grid toolbar.

4. Edit any of the following (for unpublished attributes):

Only the following fields can be edited for a previously published attribute: Name, Description, Display width, Restricted, Values must be unique, Default Value, Clear on Clone, Cascading Delete.

- **Name**: The name of the attribute.
- **Description**: Optional text describing the attribute
- **Display width**: The default number of characters that display in the grid for each value.
- **Restricted**: Restrict direct update access by end users. This data can only be changed by prescribed functions (such as approving a match or system processes like CRM). Selecting this option essentially makes an attribute read-only to all users.
- **Values must be unique** Index this attribute and identify it as unique. See [Attribute Indexing and Unique Constraints](https://support.profisee.com/wikis/profiseeplatform/attribute_indexing_and_unique_constraints) for more information concerning creating unique values.
- **System Identity for**: Make this attribute an identity attribute for a system in the external systems list.*This option is only available for text attributes when an external system is defined in the external systems list.*
- **Index for query performance**: Add the attribute to a search index.
- **Default Value:** The value this attribute defaults to when a new member is created within Profisee FastApp Portal and this attribute is included in the associated form. This value is not altered for pre-existing members.
- **Clear on clone**: Clears the value for this attribute when members are cloned.
- **Cascading Delete**: When a parent record is deleted, all child records are deleted as well. Because this can result in massive loss of data, this setting is not recommended for most users.

5. Click **Save**.

The edited attribute appears in the tree view pane as a change. In the modeling grid, the edited attribute appears shaded a different color. When the model is saved, the standard attribute icon displays, and the shading in the grid disappears.