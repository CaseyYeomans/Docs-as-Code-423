# Special Considerations for using the REST API

When using the Profisee REST API, observe the following to ensure your environment does not encounter issues with the API.

## Special Characters

When specifying a single member code in the route of the member's Get request, some special characters are not supported. Using any of the following characters (even if using an escape sequence) will result in an error.

| | | |
| --- | --- | --- |
| **Character** | **Name** | **Note** |
| **:** | Colon | Even if escaped as %3A |
| **%** | Percent | Even if escaped as %25 |
| **&** | Ampersand | Even if escaped as %26 |
| **>** | Greater than | Even if escaped as %3E |
| **<** | Less than | Even if escaped as %3C |
| **?** | Question mark | Even if escaped as %3F |
| **+** | Plus sign | Even if escaped as %2B |
| **/** | Forward slash | Even if escaped as %2F |
| **\** | Back slash | Even if escaped as %5C |

To avoid these errors, use the **Codes** parameter to specify the code of the member with special characters instead of specifying the member in the route.

## Additional or Obsolete Properties Returned

When making a request, you may see non-requested properties returned in addition to the requested properties. In some cases, these properties may be obsolete for the API version in use. These properties are returned for legacy users and to better accommodate backwards compatibility. No error has occurred, and no action is needed to resolve this.

## Batching Performance Considerations

To ensure optimal performance, it is recommended to limit your Get Record request page size to a maximum of 10,000. When sending in Post or Patch request, records should be sent in batches no larger than 50,000. The number of attributes in the entity impacts performance. A get request that includes 25 attributes is about 3 times faster than a get request that includes 100 attributes, and is 6 times faster than a get request that includes 200 attributes. Post and Patch requests behave similarly as far as number of attributes included in the request.

This should not be confused with the *Batch size to send* system setting, which is also set to a recommended 50,000 records. This setting is for SQL transactions and not REST calls.

## Attributes Returned Based on Permissions

If the user making the call does not have adequate permissions to view an attribute, the attribute is not returned in the data quality validation status list.