# GetMember, GetEntity, and GetAttribute Responses

The following tables are a comprehensive listing of the response codes that may be returned for members, entities, and attributes. Note that you may encounter additional responses that are not listed here. These responses are legacy properties and are no longer used.

## GetMember/GetRecord Responses

| | |
| --- | --- |
| **Response** | **Description** |
| ValidationIssueClauseIds | Returns a key value pair of the attribute name that violated a rule and the id of the rule. For version 1 of the gateway, there is not a way to get back more information about the rule from the rest endpoint. |
| CanUpdate | User has permissions to update the record. |
| CanDelete | User has permissions to delete the record. |
| **GetMember properties outside the data collection** | |
| totalRecords | Total number of records in the result, including any filter applied. |
| pageNumber | Page number of the result. |
| pageSize | Page size requested. |
| ResultCount | The result count for the page requested. Will not exceed the pageSize. |
| TotalPages | Total number of pages in the result based on pageSize requested. Result is 1 when a single member is requested. |
| PreviousPage | The URL link to retrieve the previous page of records. This response is null when single member requested. This response can also be null if it is the first page of multiple pages. |
| NextPage | The URL link to retrieve the next page of records. This response is null when a single member is requested. This response can also be null if on the last page of multiple pages. |

## GetEntity Responses

| | |
| --- | --- |
| **Response** | **Description** |
| CodeGenerationSeed | Create code values automatically starting with this value. |
| isCodeGenerationEnabled | Create code values automatically. |
| fileCategories | Refers to the File Attachment microservice. |

## GetAttribute Responses

| | |
| --- | --- |
| **Response** | **Description** |
| Displaywidth | Value of the **Display width** property in a Fast App studio entity grid. |
| domainEntityId | The domain entity this DBA points to. |
| isRestricted | Value updates by users are not allowed; only the system can set values. |
| displayOrder | Display order in Fast App studio entity grid. |
| externalsystem | Alternate key from external system. |
| domainEntityIsSytemAware | The domain entity this DBA points to is system aware (has system aware attributes). |
| IsClearonClone | Controls UI behavior to clear value when member is cloned. |
| IsIndexed | Attribute is indexed. |
| IsUnique | Value must be unique. |
| hasDefault | Controls UI behavior to populate value from Portal when member is created. |

### See more

[REST Status Codes](https://support.profisee.com/wikis/profiseeplatform/rest_status_codes)