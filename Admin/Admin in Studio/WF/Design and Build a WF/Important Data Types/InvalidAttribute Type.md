# InvalidAttribute Type

The **InvalidAttribute** type is a subclassification of the [Attribute](http://support.profisee.com/wikis/profiseeplatform/attribute_data_type) data type that is available via the **InvalidAttributes** list on the [Member](http://support.profisee.com/wikis/profiseeplatform/member_data_type) object when read from the server.

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts.MasterDataServices

### Properties

| | | |
| --- | --- | --- |
| **Property Name** | **Data Type** | **Description** |
| IsConstraintViolation | bool | Specifies if the associated attribute's value violates a data quality constraint rule. |

### Remarks

The **InvalidAttribute** type is a subclassification the [Attribute](http://support.profisee.com/wikis/profiseeplatform/attribute_data_type) type. When an attribute fails a data quality constraint rule, it replaces the standard **Attribute** object in the member record's **Attributes** collection.

### See Also

- [Attribute Type](http://support.profisee.com/wikis/profiseeplatform/attribute_data_type)
- [Member](https://support.profisee.com/wikis/profiseeplatform/member_data_type)