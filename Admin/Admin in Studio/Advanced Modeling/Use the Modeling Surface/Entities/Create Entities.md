# Create Entities

Entities are model objects containing data members (rows in the entity grid view) and attributes (columns in the entity grid view). When an entity is first created, it contains no members and only two attributes--Name and Code.

Create an entity in Advanced Modeling:

1. Expand the model to the **Entities** container.
2. Do one of the following:

1. In the model tree, right-click **Entities**.
2. Click **Create** on the menu, **-or-**
3. In the model tree, select **Entities**.
4. Click inside the modeling grid, and then click the plus sign on the modeling grid toolbar.

The **Create Entity** dialog appears.

3. Enter the information for the new entity:

- **Name**: The name of the entity
- **Description**: An optional description of the entity
- **Primary key attribute**: The attribute in the entity used to uniquely identify rows. By default, this is Code.
- **Primary name attribute**: The attribute in the entity used hold additional information to identify rows, but which is not necessarily unique. By default, this is Name.
- **Create Code values automatically**: Generates code values for data members
- **Starts with**: Used with the **Create Code values automatically** option. Determines the initial value for automatically generated codes.
4. Click **Save**.

The new entity appears in the tree view pane as a change. In the modeling grid, the new entity appears in a row shaded yellow. After the model is saved, the standard entity icon displays, and the yellow shading in the grid clears.

All new entities are created with only the Name and Code attributes, and no members or values.