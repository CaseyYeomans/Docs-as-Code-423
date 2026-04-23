# Relationship List Control

The Relationship List displays the child members of the initiating member in a grid layout, similar to the entity grid in Profisee. This control can include the options to Add, Open, or Delete members.

The Relationship List control contains the following properties which can be configured for the purposes of your form:

| Property | Property Option | Description |
| --- | --- | --- |
| **Relationship** | | | | --- | | Relationship (list of entities) | | The Relationship property displays a list of entities where the domain referenced by a DBA is the entity in the form model context. Example: If you created a form for the Color entity in the model Product, the Relationship list would display all model entities where the Color entity is a domain for a DBA in those entities. The DBAs are links between Color and the other entities. The members that display in the form are those that are children of the initiating member. If the initiating member in the Color entity had a value of Blue, all of the members displaying in the form would have a value of Blue for the Color DBA. |
| Behavior | Add - Allow (True | False) | True: User can add members to the entity referenced by the control; Add button displays. False: User cannot add members to the entity; Add button does not display. |
| | | | | --- | | Add - Form (list of forms) | | Selects the form that is used for adding new members. Note: This property is disabled if you have specified a Many to Many relationship. Many to Many relationships use a bulk add feature and do not require a form for adding. |
| | Add - Form Name (text) | Defines the title of the Add Form. Note: This property is disabled if you have specified a Many to Many relationship. Many to Many relationships use a bulk add feature and do not require a form for adding. |
| | Add - Presentation View (list of presentation views) | Selects the presentation view that is used to display the Bulk Add for a Many-to-Many relationship. The Bulk Add allows you to add items to your relationship list from the second entity in your relationship. If left blank, it will use the Columns property to define the columns that are displayed. Example: If you have a Many-to-Many relationship for "Product" and "Vendor," a relationship list control for a form on the Product entity will display only presentation views for the Vendor entity. |
| | Delete - Allow (True | False) | True: User can delete members on the form, and the Delete button displays. False: User cannot delete, and the Delete button does not display. |
| | Open - Allow (True | False) | True: User can edit members on the form, and the Open button displays. False: User cannot edit members on the form, and the Open button does not display. |
| | Open - Form (list of forms) | Defines the form that is used for editing displayed members. |
| | Open - Form Name (text) | Defines the title of the Open Form. |
| Display | Assign Presentation View (list of presentation views) | Optionally controls the way the list is displayed. If left blank, Name and Code are displayed in ascending order. Note: For a Many-to-Many relationship, only presentation views that have been configured for the bridge entity are available. Otherwise, presentation views created for a child entity are available. |
| | Columns (Attribute selection dialogue) | Defines the attributes to display in the grid. When you click the ellipsis (...) button in the Columns row, the Column Selection dialog appears. Select the attributes from the Available Attributes column and move them to the Selected Attributes column using the arrow buttons. The Selected Attributes define the attributes that display as attribute columns in the form. To set the widths of the columns, select each attribute in the Selected Attributes column and type a width for it (in pixels) in the Width field. |
| | Display Format (Name | Code | CodeName | NameCode) | Determines the format of the member Name and Code values. |
| | Grid Height (pixels) | Defines the vertical size of the grid when it is rendered in HTML. |
| | Label (text) | Defines the label text. |
| Layout | Maximum Width (pixels) | Defines the maximum width of the control. |
| | Minimum Width (pixels) | Defines the minimum width of the control. A minimum width of 0 causes the control to automatically resize. The control still displays. Do not set the control minimum width to 0 to prevent a control from displaying. |