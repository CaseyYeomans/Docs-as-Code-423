# ValidationStatus Enumeration

The **ValidationStatus** enumeration identifies the quality status of the member attribute to which it is associated.

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts.MasterDataServices

### Properties

| | |
| --- | --- |
| **Enumeration Value** | **Description** |
| Unknown=0 | The validation status of the member or attribute is unknown. |
| ValidationSucceeded=1 | The data quality rules have been run and no errors have been reported for the associated attribute or member record. |
| ValidationFailed=2 | The data quality rules have been run and at least 1 error has been detected on the associated attribute or member record. |

### Remarks

The **ValidationStatus** enumeration is set on a per attribute basis when a [Member](http://support.profisee.com/wikis/profiseeplatform/member_data_type) is returned to a caller through the API of via a workflow activity. The validation status of the **Code** and **Name** attributes of a member are included in the [MemberIdentifier](http://support.profisee.com/wikis/profiseeplatform/memberidentifier_type) type in the **CodeValidationStatus** and **NameValidationStatus** properties respectively.

### See Also

- [Attribute](https://support.profisee.com/wikis/profiseeplatform/attribute_data_type)
- [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type)
- [MemberIdentifier](https://support.profisee.com/wikis/profiseeplatform/memberidentifier_type)