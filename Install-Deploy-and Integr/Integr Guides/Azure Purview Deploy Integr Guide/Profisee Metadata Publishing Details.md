# Profisee Metadata Publishing Details

Profisee publishes five types of artifacts to Azure Purview:

1. A single**Profisee Instance** definition is published to Purview for each Profisee instance (i.e. Profisee cluster) that is installed and registered with Purview.

2. For each **Profisee Instance**, a collection of zero or more Profisee Entity definitions are published to Purview.

3. For each **Profisee Entity**, 2 or more Profisee Attribute definitions are published to Purview. Each definition contains the Name and Code attributes of the entity plus any additional user-defined attributes that have been defined for the entity.
4. For each **Profisee Relationship,** a relationship asset is created in Purivew that describes the type of relationship and its properties.
5. For each **Profisee Hierarchy**, a hierarchy asset is created in Purview that describes the type of hierarchy and its properties.

Profisee Instance details are published to Purview during the instance registration process that occurs during the initial start-up process of the Profisee cluster. On first start-up, Profisee checked to see if it has registered itself with Purview and, if not, it registers the Profisee Instance definition. If a model (i.e. entities and attributes) already exists for the Profisee instance, then the metadata associated with the entities and attributes are also published to Purview immediately after instance registration.

After the initial synchronization of the model artifacts, incremental updates occur when subsequent data modeling activities occur. Any time entities or attributes are added, updated, or deleted from the master data model in Profisee, these changes are synchronized to Purview.

The details of each published artifact are defined in the following subtopics.

### Profisee Instance Definition

The table below details the metadata that are published to Purview that describe the Profisee Platform instance.

| | |
| --- | --- |
| **Property** | **Description** |
| **mdmAssetGuid** | The globally unique identifier assigned for a Profisee cluster instance. |
| **Name** | The instance name in the format: "Profisee ({External\_Url})" |
| **Qualified Name** | Identical as the Name property |
| **URL** | The fully-qualified external DNS name to which the license is associated. |
| **mdmCreatedDateTime** | The date and time the instance was created in Purview. |
| **mdmUpdatedDateTime** | The date and time the instance was last updated in Purview. |
| **mdmCreatedByUser** | The Profisee Governance service that creates the instance. |
| **mdmUpdatedByUser** | The Profisee Governance service that updates the instance. |
| **productVersion** | The version of the Profisee Platform running on this instance |
| **restGatewayUrl** | URL link to access the Profisee REST Gateway |

An additional section labeled **Properties - Advanced** links to all entities in this Profisee instance.

### Profisee Entity Definition

The table below details the metadata that are published to Purview that describes each Profisee entity.

| | |
| --- | --- |
| **Property** | **Description** |
| **Name** | The name as specified during master data model development for the entity. |
| **mdmAssetGuid** | The globally unique identifier assigned by Profisee for an entity. |
| **qualifiedName** | A globally unique name for this entity in the format: {Profisee\_Intance\_FQN}/{Entity mdmAssetGuid} |
| **isKeyGenerationEnabled** | Displays **Yes** if the MDM entity is configured to automatically generate a unique Code value when a new record is created in the entity. **No** indicates that the creator of a record is responsible for supplying the unique code value. |
| **keyGenerationSeed** | The configured starting value used when generating new Code values for this entity. The Code Generation Seed is null/empty if the Code Generation Enabled is set to No. |
| **hasFileAttachmentCategories** | Set to **Yes** if file attachment categories have been created for this entity. Otherwise, this is set to **No**. |
| **mdmCreatedByUser** | The date and time the entity was created. |
| **mdmCreatedDateTime** | The username responsible for the creation of the entity in Profisee. |
| **mdmUpdatedDateTime** | The date and time the entity was last updated. |
| **mdmUpdatedByUser** | The username responsible for the last update to the entity in Profisee. |
| **Properties - Advanced** | |
| **DomainBasedAttributes** | Links to domain based attributes where this entity is used as the domain entity. |
| **Instance** | Links to the Profisee instance that contains this entity. |

### Profisee Attribute Definition

The table below details the metadata that are published to Purview that describes each Profisee attribute.

| | |
| --- | --- |
| **Property** | **Description** |
| **mdmAssetGuid** | The globally unique identifier assigned by Profisee for an attribute. |
| **Name** | The name as specified during master data model development for the attribute. |
| **qualifiedName** | A globally unique name for this attribute in the format: {Profisee\_Intance\_FQN}/{Entity mdmAssetGuid}/{Attribute mdmAssetGuid} |
| **type** | Specifies the attribute's data type. The following values are possible: - **Text**: A text or string attribute of maximum length specified by the maximumTextLength property. - **Number**: A numeric attribute with decimal precision specified by the decimalPrecision property. - **Domain List**: The value is of a text format but the value of this attribute is constrained by the values in the related MdmEntity. - **URL**: The value is a string but is expected to be a valid URL (typically but not exclusively a http/https hyperlink). - **Date**: The value is a date value. Date values do not include a time component and should not be affected by time zones. - **DateTime**: The values for this field are time values inclusive of the date component. Such value are relative to the time zone. Profisee maintains DateTime values in UTC format. Consumers should shift the time to the relative location of the consumer/client. |
| **textLength** | When the attribute is of type Text or URL, this represents the maximum allowable length of text that can appear in this attribute. |
| **decimalPrecision** | The maximum number of digits that appear behind the decimal point. This value is relevant for attributes of type Number only. |
| **clearwhenCloned** | Open when cloning records in Fast App Studio to clear the value for this attribute on the newly created record. |
| **isDomainEntitySystemAware** | Whether the domain entity has an attribute that is a system-aware attribute. |
| **isIndexed** | Will be **true** if this attribute has an index defined in Profisee |
| **isRestricted** | Whether this attribute can be updated by a user in the Profisee Platform |
| **isUnique** | Whether there can be more than one record with the same attribute value |
| **mdmCreatedOnDateTime** | The date and time the entity was created. |
| **mdmCreatedByUser** | The user that created the entity. |
| **mdmUpdatedDateTime** | The date and time the entity was last updated. |
| **mdmLastUpdatedByUser** | The user that last updated the entity. |
| **Properties - Advanced** | |
| **DomainEntity** | For domain based attributes, links to the domain entity used for this attribute. |
| **Entity** | Links to the entity where the attribute is defined. |