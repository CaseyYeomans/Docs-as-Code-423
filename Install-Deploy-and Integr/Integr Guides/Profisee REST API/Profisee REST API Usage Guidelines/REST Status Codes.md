# REST Status Codes

| | |
| --- | --- |
| **HTTP Status Code** | **Description** |
| **200 Success** | The request record has been successfully updated for a given entity. |
| **201 Resource Created** | The requested record has been successfully created for a given entity, if the record does not exist. |
| **202 Accepted** | The request has been received and the requested action is in-progress. |
| **204 No Content** | The request has succeeded, but there is no content to send for this request. |
| **207 Multiple Status** | Records were created or updated, but some errors were encountered during creation. |
| **400 Bad Request** | One or more validation errors occurred. |
| **401 Unauthorized** | You are not authorized to access this resource. |
| **404 Not Found** | The requested entity could not be found. |
| **500 Internal Server Error** | An unexpected error occurred on the server. Please check your Profisee logs for more details. |

### See more

[GetMember, GetEntity, and GetAttribute Responses](https://support.profisee.com/wikis/profiseeplatform/member_entity_and_attribute_responses)