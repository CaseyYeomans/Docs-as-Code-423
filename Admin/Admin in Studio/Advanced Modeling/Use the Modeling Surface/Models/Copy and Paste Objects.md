# Copy and Paste Objects

Move objects in the following ways:

- Tree to tree
- Tree to grid
- Grid to tree
- Grid to grid

Moves can occur within the same model or between different models.

Advanced Modeling only allows valid object moves. For example, you cannot move an entity to an attribute, or copy an attribute to a model.

Copy and paste moves include the following:

| Model component: | Valid moves to objects: | Valid moves to containers: |
| --- | --- | --- |
| **Model** | None | None |
| **Container node** | None | None |
| **Entity** | Model Entity (creates DBA) | Entities container Attributes container (creates DBA) |
| **Attribute** | Entity Attribute - Copy to create another attribute in a specific position - Reposition in list of attributes | Attributes container |
| **Code and Name Attributes** | None | None |