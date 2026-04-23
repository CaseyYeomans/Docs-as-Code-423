# Record Type

The **Record** class represents the value of a record record within an entity when read from or updating the record in the associated entity.

**Namespace**: Profisee.MasterDataMaestro.Services.DataContracts.MasterDataServices

### Properties

|  |  |  |  |
| --- | --- | --- | --- |
|  | **Property Name** | **Data Type** | **Description** |
|  | Id | Guid | A Globally-Unique Identifier (GUID) associated with this record record within its associated entity.  *Inherited from Identifier* |
|  | InternalId | int | The Profisee instance-specific ID (surrogate key) for this record record in the entity.  *Inherited from Identifier* |
|  | Name | string | The name given to this record.  *Inherited from Identifier* |
|  | RecordId | [RecordIdentifier](http://support.profisee.com/wikis/profiseeplatform_2020_r1/memberidentifier_type) | Identifies all of the critical identifying attributes of the record when read from the database. It includes the **Id**, **InternalId**, **Name**, and **Code** as specified above. It is important to note that these properties are just shortcut names to the underlying properties of the **RecordIdentifier**. |
|  | IsReferenceValid | bool | Indicates if the associated Id is valid. This is only used for metadata identifiers (e.g. [MaestroIdentifier](http://support.profisee.com/wikis/profiseeplatform_2020_r1/maestroidentifier_type)) and is not used for [RecordIdentifier](http://support.profisee.com/wikis/profiseeplatform_2020_r1/memberidentifier_type) instances.  *Inherited from Identifier*    **NOTE:** This field is not relevant for the **Record** class and can be ignored. |
|  | ValidationStatus | [ValidationStatus](http://support.profisee.com/wikis/profiseeplatform_2020_r1/validationstatus_enumeration) | Indicates the validation status of this record record. |
|  | Attributes | Collection<[Attribute](http://support.profisee.com/wikis/profiseeplatform_2020_r1/attribute_data_type)> | The complete collection of attributes that are part of this record record. The set of attributes in the collection is determined by the attributes requested in the read operation or the attributes placed into the collection by the client when creating a new record records to be added to the associated entity. |
| \* | ValidAttributes | List<[Attribute](http://support.profisee.com/wikis/profiseeplatform_2020_r1/attribute_data_type)> | The collection of attributes for which there are no identified data quality issues. |
| \* | InvalidAttributes | List<[InvalidAttribute](http://support.profisee.com/wikis/profiseeplatform_2020_r1/invalidattribute_type)> | The collection of attributes for which a data quality issue has been detected. |
| \* | IndeterminateAttributes | List<[Attribute](http://support.profisee.com/wikis/profiseeplatform_2020_r1/attribute_data_type)> | The collection of attributes where the status has not been determined because the validation issue status was not requested as part of the read operation or attributes that were set in the **Attributes** collection after the read has occurred. In the latter case, since the value is set by the client, it is considered indeterminate because rules have not been run because the record or update has not yet been published to the server. |
|  | TotalValidationIssueCount | int | The total number of validation issues associated with this record record. |
|  | SecuredValidationIssueCount | int | The count of validation issues associated with this record for which the current user being serviced by the client has no security rights. |
|  | UpdateState | [UpdateStateType](http://support.profisee.com/wikis/profiseeplatform_2020_r1/updatestate_enumeration) | An enumeration that identifies to the server if the record is to be added, modified, or deleted based on changes made by the client prior to being published to the server. |
|  | SecurityPermission | [SecurityPermission](http://support.profisee.com/wikis/profiseeplatform_2020_r1/securitypermission_enumeration) | Identifies the record-level security rights granted to the reader for the record record. |
|  | AuditInfo | [AuditInfo](http://support.profisee.com/wikis/profiseeplatform_2020_r1/auditinfo_type) | Contains the audit details for this specific record. This includes the date and time as well as the users that created and last updated the record record. |
|  | TransactionAnnotation | string | A text annotation of a change made for this specific record  **NOTE:** This property is obsolete and should not be used or referenced. It is an artifact used for legacy Microsoft Master Data Services (MDS) support is not relevant in a Profisee Platform model. |
|  | Parents | Parent | Identifies parent records in the legacy MDS architecture.  **NOTE:** This property is obsolete and should not be used or referenced. It is an artifact used for legacy Microsoft Master Data Services (MDS) support is not relevant in a Profisee Platform model. |

\* *Getter only*

### Remarks

The **Record** type represents a record that has been read or is to be added, updated, or deleted from its associated entity. The record record’s values are provided in the **Attributes** collection which is of type Collection<[Attribute](http://support.profisee.com/wikis/profiseeplatform_2020_r1/attribute_data_type)>. The record record’s identifying attributes are provided in the **RecordId** property.

It is important to note that the **Attributes** collection contains only those attributes that are requested on the read operation. The client has the option of:

* Reading only the **RecordId**
* Reading only a specified set of attributes
* Reading all attributes associated with the entity

When a record record is read, the **RecordId** property tethers the record to source record in the entity through the **InternalId** which is the surrogate key for that record in the table associated with the entity. The **Code** and **Name** attributes ***are not*** included in the **Attributes** collection on a read operation. However, if the client wishes to change the **Code** or **Name** attributes, an [Attribute](http://support.profisee.com/wikis/profiseeplatform_2020_r1/attribute_data_type) object that is associated with the **Code** or **Name** attribute must be added to the **Attributes** collection as part of the update or merge (upsert) operation.

The client assesses the quality of the record record by examining the **TotalValidationIssueCount** and **SecuredValidationIssueCount** respectively. In addition, the list of invalid attributes can be obtained from the **InvalidAttributes** list. Conversely, the valid attributes can be found in the **ValidAttributes** list.

Audit information is available in the **AuditInfo** property.

---

### See Also

* [Attribute Type](http://support.profisee.com/wikis/profiseeplatform_2020_r1/attribute_data_type)
* [AuditInfo Type](http://support.profisee.com/wikis/profiseeplatform_2020_r1/auditinfo_type)
* [InvalidAttribute Type](http://support.profisee.com/wikis/profiseeplatform_2020_r1/invalidattribute_type)
* [RecordIdentifier Type](http://support.profisee.com/wikis/profiseeplatform_2020_r1/memberidentifier_type)
* [SecurityPermission Type](http://support.profisee.com/wikis/profiseeplatform_2020_r1/securitypermissiontype_enumeration)
* [UpdateState Enumeration](http://support.profisee.com/wikis/profiseeplatform_2020_r1/updatestate_enumeration)
* [ValidationStatus Enumeration](http://support.profisee.com/wikis/profiseeplatform_2020_r1/validationstatus_enumeration)