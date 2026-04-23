# MultiLevelContext Type

The **MultiLevelContext** represents the path from a member record to a value that is stored within the [Attribute](http://support.profisee.com/wikis/profiseeplatform/attribute_data_type) to which this **MultiLevelContext** is contained.

**Namespace**: Profisee.MasterDataMaestro.Services.Contracts.DataContracts

### Properties

| | | |
| --- | --- | --- |
| **Property Name** | **Data Type** | **Description** |
| Levels | List<[MetadataAttribute](http://support.profisee.com/wikis/profiseeplatform/metadataattribute_type)> | Specifies the list of Domain-based Attributes (DBA) that represent a path from the entity associated with the Member record to the Attribute to which this **MultiLevelContext** is associated. |

### Remarks

When a read operation is performed on an entity, the reader (i.e. client) can request attributes that do not exist on the directly on the entity but, instead, are accessible via a **Multi-level Attribute (MLA)** path. The **MultiLevelContext** property of the [Attribute](http://support.profisee.com/wikis/profiseeplatform/attribute_data_type) class represents this path.

The **MultiLevelContext** contains a list of [MetadataAttribute](http://support.profisee.com/wikis/profiseeplatform/metadataattribute_type) objects where each entry in the list (beginning at Levels[0]) represents a step in the path to the target attribute whose value is stored in the associated [Attribute](http://support.profisee.com/wikis/profiseeplatform/attribute_data_type) object. For example, the following path would represent the path from a Customer entity to the name of the territory manager that is responsible for the Customer account.

Customer.Territory.Manager.Name

In this case, the [Attribute](http://support.profisee.com/wikis/profiseeplatform/attribute_data_type) contained in the [Member](http://support.profisee.com/wikis/profiseeplatform/member_data_type) object's **Attributes** collection would contain the territory manager's name and the path to that name would contain the following **Levels**:

**Levels[0]**: Territory attribute of the Customer entity

**Levels[1]**: Manager attribute of the Territory entity

### See Also

- [Attribute Type](http://support.profisee.com/wikis/profiseeplatform/attribute_data_type)
- [Member Type](https://support.profisee.com/wikis/profiseeplatform/member_data_type)
- [MetadataAttribute Type](https://support.profisee.com/wikis/profiseeplatform/metadataattribute_type)