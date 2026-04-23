# CreateSetAddRecord

The CreateSetAddRecord activity Creates a new Record using the RecordDataContext provided.

| | | |
| --- | --- | --- |
| **CreateSetAddRecord In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| RecordDataContext\* | [RecordDataContext](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type) | A **RecordDataContext** object containing information required for the activity. |
| Name | String | A **String** representing the Name of the Record. |
| Code | String | A **String** representing the Code of the Record. |
| RecordValues | Dictionary<string, object> | A **Dictionary<String,Object>** object holding the <Attributes,Values> to designate an Attribute value. |
| **CreateSetAddRecord Out Arguments** | | |
| Errors | Collection<Error> | A **Collection<Errors>** that returns if there are any issues within the activity. |
| RecordIdentifier | [RecordIdentifier](http://support.profisee.com/wikis/profiseeplatform/memberidentifier_type) | The **RecordIdentifier** object that is returned. |

*\*Argument is required*

### Remarks

The Name, Code, and any other values included are set on the Record before it is added to the repository. This activity creates and sets values for a record and adds the Record to the database that is associated with the RecordDataContext. The object returned is a RecordIdentifier.

### See Also

- [RecordIdentifier](https://support.profisee.com/wikis/profiseeplatform/memberidentifier_type)
- [RecordDataContext](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type)