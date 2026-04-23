# GetRecord

The GetRecord activity reads a specified record record from an Entity based on the **EntityId** and **Code** value specified in the **RecordDataContext** argument.

| | | |
| --- | --- | --- |
| **GetRecord In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| RecordDataContext\* | [RecordDataContext](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type) | Specifies the key used to read a specific record from an entity. |
| AttributeNames | Collection<string> | A collection of attributes names to include when the record is read. If this argument is **null**, then all attributes are included. If this argument is an empty collection, then the record returns only the **RecordId** for the specified record. |
| **GetRecord Out Arguments** | | |
| Result | [Record](http://support.profisee.com/wikis/profiseeplatform/member_data_type) | The record record containing the identifier and attributes as specified by the **AttributeNames** input argument. If ValidationIssues was set to true then a dictionary of attributes and their issues is returned with the operation result. A **null** value is returned if the record specified in the **RecordDataContext** input argument could not be found. |

*\*Argument is required*

### Remarks

The **GetRecord** activity reads a record from the Profisee server and returns the record in the form of a **Record** object. The returned record identifies its key in the **RecordIdentifier** property. The values of its attributes are included in the record's Attributes collection. If the user provided a Collection<Attribute>, the returned record Attributes will consist of only those Attributes. If the user set GetValidationIssues to true, then a Dictionary of attributes with issues will be returned with the operation result. If the **RecordId** specified in the **RecordDataContext** argument does not exist, the activity returns a **null** result.

### See Also

- [G](https://support.profisee.com/wikis/profiseeplatform/new_member_data_context_activity)[et Records](https://support.profisee.com/wikis/profiseeplatform/get_members)
- [Record](https://support.profisee.com/wikis/profiseeplatform/member_data_type)
- [Record Data Context](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type)