# Field Control

A field displays the value for a selected attribute in an entity. The way the information displays depends on the type of attribute--a DBA displays in a list, for example, while a text attribute displays in a text box. The attribute value for the initiating member displays by default.

Multi-level attributes are handled differently and must be configured using the [Multi-level Attribute Field Control](https://support.profisee.com/wikis/profiseeplatform/multi-level_attribute_field_control).

To configure the field control, select it in the Layout panel and edit the options in the Display panel. Note that the displayed properties are different for different free-form attributes and domain-based attributes (DBAs).

The Field control offers an additional option to use parent attributes to create cascading fields in the form. For more information, see [Using Parent Field Relationships in Forms](https://support.profisee.com/wikis/profiseeplatform/use_parent_field_relationships_in_forms).

| Property | Property Option | Description |
| --- | --- | --- |
| **Attribute** | Attribute (list of attributes) | |
| **Behavior** | AI Role (None | Input | Output) | Determines if this form is an Input field or an Output field. Input fields are used to feed Open AI information, and no suggestions will appear for this field. Output fields do not feed information to Open AI, and suggestions are provided for them. This option can only be used in instances with configured [Open AI system settings](https://support.profisee.com/wikis/profiseeplatform/open_AI), but is displayed in all instances. |
| | Enabled Condition Field (Dropdown) | The field that conditionally enables this field when the specified value is provided. |
| | Enabled Condition Value (Dropdown) | The value that enables the specified field. |
| | Enabled (True | False) | |
| | Field Description (Optional) (Text) | A plain-text description of the entity that is used to give the Open AI model a baseline of information for the entity. This description will not display to users. |
| | Multiline (True | False) | Note: Multiline is an available property only when a text free-form attribute is selected. |
| | Required (True | False) | |
| | Valid (True | False) | Indicates if the attribute value does not pass data quality rule validation when saved. |
| **Data** | Add - Form (Form) | |
| | Add - Form Name (Text) | |
| | Edit Form | |
| | Edit Form Name (Text) | |
| | Presentation View (Presentation View) | |
| **Display** | Display Format (Name | Code | CodeName | NameCode) | |
| | Label (Text) | |
| | Label Font Color (RGB value) | |
| | Bold (True / False) | |
| | Italic (True / False) | |
| | Size (Pixel Size) | |
| | Underline (True / False) | |
| **Layout** | Column Span (number of columns) | |
| | Maximum Width (pixels) | |
| | Minimum Width (pixels) | |
| | Row Span (number of rows) | |