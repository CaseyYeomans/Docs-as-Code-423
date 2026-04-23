# Attribute Indexing and Unique Constraints

Attributes within your master data model can be configured to be indexed or indexed **and** unique. This configuration is performed via the [Create Attribute](https://support.profisee.com/wikis/profiseeplatform/create_attributes) and [Edit Attribute](https://support.profisee.com/wikis/profiseeplatform/edit_attributes) dialogs in Advanced Modeling and Adaptive Modeling.

You may want to index an attribute because applications and users typically search for information in this entity using this attribute as a key. An index will improve query performance, but does have a negative impact on create and update performance because the index must be updated during the create or update operation.

To index an attribute, you must select the **Index for query performance** option. This creates a SQL index on the specified attribute. The index is created with an ascending sort order.

You can also indicate that an attribute value must be unique across the set of values in the entity. This further enforces data integrity by preventing duplication of data for the specified attribute in the entity. If the entity is already populated with data and you attempt to create a unique constraint, the creation of the constraint fails if the existing data in the attribute is not already unique.

To create the unique constraint, you must first cleanse the data to ensure that the attribute values are unique and then attempt to create the unique constraint again. To create a unique constraint, select the **Values must be unique** option. When this option is set, you will also note that the **Index for query performance** option is also set and disabled. This is because the creation of a unique constraint requires the creation of an index. Therefore, you cannot configure the former without the latter.

Note also that the **System Identity for** option is associated with the **Values must be unique** option. The **System Identity for** option identifies the attribute as holding the [System Aware Identity Management](https://support.profisee.com/wikis/profiseeplatform/system_aware_identity_management_overview) ID for a target external system such as SAP or Salesforce. SAIM IDs, must be unique as they represent a unique key in the associated external system. Therefore, before an attribute can be a SAIM ID, it must be unique.