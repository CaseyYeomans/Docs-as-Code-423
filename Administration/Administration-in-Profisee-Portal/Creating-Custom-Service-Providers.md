# Creating Custom Service Providers

---

Profisee Connect service providers enable Profisee to integrate with external REST APIs. A service provider is a JSON artifact that contains JavaScript code for API communication and a configuration object that defines the service's inputs, outputs, authentication, and processing behavior.

This guide walks you through every step of building a service provider from scratch, from analyzing the target API to delivering a tested, importable artifact to the customer.

### 1.1 What You Will Deliver

At the end of this process, you will produce a single JSON file (the service provider artifact) that the customer imports into the Profisee Portal. This artifact contains two main components:

* Script Record: JavaScript code that calls the external API, handles errors, and maps the response into output fields.
* Service Provider Record: Configuration defining the service name, input parameters, output fields, authentication settings, and processing options.

### 1.2 Prerequisites

* Review the [Service Provider Documentation](https://github.com/Profisee/connectors/tree/main/Service%20Provider%20Documentation) available in this [GitHub repo](https://github.com/Profisee/connectors)
* Access to the target API documentation (or a working cURL command)
* A sample API response (JSON)
* Knowledge of the API's authentication method
* A text editor or IDE for writing JSON and JavaScript
* Python 3 installed (for GUID generation)
* Access to a Profisee environment for testing

### 1.3 AI Tools

Profisee has had success using tools like Claude and Copilot to develop Service Providers. This is the fastest way to approach developing custom integrations.

## 2. Gather API Information

Before writing any code, you must fully understand the API you are integrating with. Collect the following information from the customer or from the API documentation.

### 2.1 Required Information Checklist

| Item | Description | Example |
| --- | --- | --- |
| API Endpoint URL | The base URL of the API | https://api.example.com/v2/search |
| HTTP Method | GET, POST, PUT, or DELETE | GET or POST (most common) |
| Sample Request | A cURL command or request example | curl -X GET "https://api.example.com/search?q=test" |
| Sample Response | Example JSON response body | { "results": [ { "id": 1, "name": "Test" } ] } |
| Authentication Method | How the API authenticates requests | API Key, OAuth2, Basic Auth, or None |
| Rate Limits | Any request rate or concurrency limits | 100 requests/minute |

### 2.2 Authentication Decision Matrix

Determine which authentication pattern to use based on how the target API authenticates:

| Auth Type | Information Needed | How to Handle in Artifact |
| --- | --- | --- |
| None | Nothing | Omit authSettings entirely |
| API Key (Header) | Header name (e.g., X-API-Key) | Create a Service-scope Credential input; add the header in the script |
| API Key (URL) | Query parameter name (e.g., apikey) | Create a Service-scope Credential input; append to the URL in the script |
| OAuth2 | Token URL | Use authSettings with Type "OAuth2" and OAuthUrl; call getOAuthToken in script |
| Basic Auth | Username and password field names | Create Service-scope Credential inputs; build Authorization header in script |

### 2.3 Analyze the API Response

Carefully examine the sample API response to plan your outputs. Pay special attention to:

* Nested objects: You will need to navigate into nested JSON structures in your script (e.g., data.result.address.city).
* Arrays: If the response contains arrays, you must flatten them into numbered output fields (e.g., ResultName1, ResultName2, ResultName3). Decide in advance how many array items to capture.
* Null/missing fields: Plan for fields that may be absent in some responses. Use fallback values like null in your output mapping.

## 3. Plan Your Inputs and Outputs

### 3.1 Understand Input Scopes

Every input in a service provider has a scope that determines when it is evaluated and where it is configured:

| Scope | Behavior | Typical Use Cases |
| --- | --- | --- |
| Service | Configured once in the Service Configuration UI. Evaluated once per strategy invocation. Same value for all records in the batch. | API keys, base URLs, client IDs, configuration parameters, credentials |
| Data | Mapped in the Integration Strategy request mapping. Evaluated per record. Different value for each record being processed. | Customer name, address, product ID, search terms from entity attributes |

### 3.2 Input Types Reference

Choose the appropriate data type for each input:

| Type | Use For | Presenter Type | Example |
| --- | --- | --- | --- |
| String | Text values | String, Expression, or Credential | Names, addresses, IDs, API keys |
| Float | Decimal numbers | Number or Expression | Prices, percentages, coordinates |
| Integer | Whole numbers | Number or Expression | Quantities, counts, max results |
| Boolean | True/false values | Boolean | IsActive, IncludeDetails |
| Date | Date values | DateTime | StartDate, BirthDate |

### 3.3 Presenter Types

The presenter type controls how the input appears in the Profisee Portal:

* String: Simple text field. Best for Service-scope configuration values.
* Expression: Dropdown/expression editor. Best for Data-scope inputs that map to entity attributes.
* Number: Numeric field with optional min/max and decimal places.
* Boolean: Checkbox control.
* DateTime: Date/time picker. Set Controls to "Date" for date-only.
* Credential: Masked input for sensitive values like API keys. Must be Service scope.
* ParameterSet: Groups multiple Service-scope inputs into a single section in the UI.

### 3.4 Plan Your Outputs

Each output maps to a field the script returns. Outputs appear in the Integration Strategy response mapping UI where users map them to entity attributes.

* Use clear, descriptive names (e.g., "Matched Company Name" not "Output1").
* For flattened arrays, use numbered suffixes: CompanyName1, CompanyName2, CompanyName3.
* Available output types: String, Float, Integer, Boolean, Date.

> [!CAUTION]
> Array Flattening Decision : If the API returns arrays of results, decide upfront how many items to capture. Each array item becomes a separate set of numbered output fields. For example, capturing the top 3 results with Name and Score fields creates 6 outputs: Name1, Score1, Name2, Score2, Name3, Score3. Confirm this number with the customer before building the artifact.

## 4. Generate GUIDs

Every service provider artifact requires two unique GUIDs: one for the script record and one for the service provider record. The script GUID is also referenced in the service's scriptId field, linking the service to its script.

### 4.1 Generate GUIDs Using Python

Run the following command to generate two GUIDs:

```
python3 -c "import uuid; print(uuid.uuid4()); print(uuid.uuid4())"
```

Example output:

a1b2c3d4-5678-4abc-9def-123456789abc (use as Script ID)

f9e8d7c6-5432-4bba-8765-abcdef012345 (use as Service Provider ID)

> [!WARNING]
> CRITICAL : Do Not Reuse GUIDs. Every artifact must have unique GUIDs. Reusing GUIDs from another artifact will cause import conflicts. Always generate fresh GUIDs for each new service provider.

## 5. Build the Artifact JSON

The artifact is a single JSON file with a specific structure. This section explains each part of the structure and how to assemble it.

### 5.1 Top-Level Structure

The artifact has three top-level properties:

```
{
"artifactVersion": "1.5.1.0",
"scripts": [ ... ],
"serviceProviderRecord": { ... }
}
```

| Property | Type | Description |
| --- | --- | --- |
| artifactVersion | string | Always set to "1.5.1.0" |
| scripts | array | Array of script records. Typically one script per artifact. |
| serviceProviderRecord | object | The service provider configuration including inputs, outputs, auth, and processing settings. |

### 5.2 Script Record

Each script record contains the JavaScript code that will be executed. The Id must match the scriptId in the service definition.

```
"scripts": [
{
"Configuration": {
"scriptContent": "YOUR ESCAPED JAVASCRIPT CODE HERE"
},
"Id": "<SCRIPT-GUID>",
"Code": "<SCRIPT-GUID>",
"Name": "My API Script"
}
]
```

> [!NOTE]
> Script Content Escaping : The scriptContent value is a JSON string. All double quotes inside the JavaScript must be escaped as \". Newlines must be encoded as \r\n. It is strongly recommended to write your script in a normal .js file first, test the logic, and then convert it to an escaped JSON string as the final step

### 5.3 Service Provider Record

This record defines how the service appears in the Profisee Portal and contains all configuration.

```
"serviceProviderRecord": {
"Configuration": {
"workerQueueOptions": { ... },
"authSettings": { ... },     // optional
"services": { ... }
},
"Id": "<SERVICE-PROVIDER-GUID>",
"Code": "<SERVICE-PROVIDER-GUID>",
"Name": "My Service Provider",
"Type": "Script"
}
```

#### 5.3.1 Worker Queue Options

These settings control how batches are processed. For most integrations, the following defaults work well:

```
"workerQueueOptions": {
"workerCount": 2,
"priorityQueueThreshold": {
"maxJobCount": 1,
"maxRecordCount": 5000
}
}
```

Increase workerCount for high-volume integrations. The priorityQueueThreshold determines which smaller batches get priority processing.

#### 5.3.2 Auth Settings (Optional)

Include authSettings only if the API uses OAuth2 authentication. When present, the Profisee Portal will display an Authentication section in the service configuration UI.

```
"authSettings": {
"Type": "OAuth2",
"OAuthUrl": "https://oauth.example.com/token"
}
```

If you leave OAuthUrl empty, the user will be prompted to enter it during service configuration.

#### 5.3.3 Services Dictionary

The services dictionary defines one or more executable operations. Each key is an internal identifier (not displayed). Most artifacts have a single service.

```
"services": {
"MyService": {
"name": "Display Name in Portal",
"description": "What this service does",
"inputs": { ... },
"outputs": { ... },
"scriptId": "<SCRIPT-GUID>",
"maximumRecordsPerRequest": 1
}
}
```

> [!NOTE]
> Set the maximumRecordsPerRequest to 1 for APIs that process one record at a time (most common). Set higher for batch APIs that accept multiple records per call. This value controls how many records appear in the input.records array.

## 6. Define Inputs in Detail

This section provides the exact JSON patterns for each type of input you may need.

### 6.1 Service-Scope Text Input

Use for configuration values like base URLs or static parameters.

```
"BaseUrl": {
"type": "String",
"scope": "Service",
"friendlyName": "API Base URL",
"presenterConfiguration": {
"type": "String",
"settings": {}
},
"isRequired": true,
"isReadOnly": false
}
```

### 6.2 Service-Scope Credential Input

Use for sensitive values like API keys. The Credential presenter masks the input in the UI.

```
"ApiKey": {
"type": "String",
"scope": "Service",
"friendlyName": "API Key",
"presenterConfiguration": {
"type": "Credential",
"settings": {}
},
"isRequired": true,
"isReadOnly": false
}
```

### 6.3 Service-Scope Read-Only Input with Default Value

Use for fixed values that should not be changed by the user.

```
"MaxResults": {
"type": "String",
"scope": "Service",
"friendlyName": "Maximum Results",
"presenterConfiguration": {
"type": "String"
},
"defaultValue": {
"name": "MaxResults",
"dataType": "string",
"assignmentType": "Literal",
"value": "3"
},
"isRequired": false,
"isReadOnly": true
}
```

### 6.4 Data-Scope Expression Input

Use for per-record values that are mapped from entity attributes in the Integration Strategy.

```
"CompanyName": {
"type": "String",
"scope": "Data",
"friendlyName": "Company Name",
"presenterConfiguration": {
"type": "Expression",
"settings": {}
},
"isRequired": true,
"isReadOnly": false
}
```

### 6.5 Grouping Service Inputs with ParameterSet

Use ParameterSet to group related Service-scope inputs into a section in the UI. Define the individual inputs separately, then reference them in the ParameterSet.

```
"ConfigurationSection": {
"scope": "Service",
"friendlyName": "Configuration Settings",
"presenterConfiguration": {
"type": "ParameterSet",
"settings": {
"Parameters": {
"Param1": "BaseUrl",
"Param2": "MaxResults"
}
}
}
}
```

The values in the Parameters dictionary ("BaseUrl", "MaxResults") must match the keys of other inputs defined in the same inputs dictionary.

## 7. Define Outputs

Outputs define the data your script returns. Each output becomes available in the Integration Strategy response mapping.

### 7.1 Output Format

```
"outputs": {
"MatchedName": { "name": "Matched Company Name", "type": "String" },
"ConfidenceScore": { "name": "Confidence Score", "type": "Float" },
"MatchDate": { "name": "Match Date", "type": "Date" },
"IsExactMatch": { "name": "Is Exact Match", "type": "Boolean" },
"MatchCount": { "name": "Match Count", "type": "Integer" }
}
```

The dictionary key (e.g., "MatchedName") is what your script must return in its output records. The "name" value is the label displayed in the Portal.

### 7.2 Flattened Array Output Example

If the API returns an array and you are capturing the top 3 results:

```
"outputs": {
"ResultName1": { "name": "Result 1 - Name", "type": "String" },
"ResultScore1": { "name": "Result 1 - Score", "type": "Float" },
"ResultName2": { "name": "Result 2 - Name", "type": "String" },
"ResultScore2": { "name": "Result 2 - Score", "type": "Float" },
"ResultName3": { "name": "Result 3 - Name", "type": "String" },
"ResultScore3": { "name": "Result 3 - Score", "type": "Float" }
}
```

## 8. Write the JavaScript Script

The script is the heart of the service provider. It receives input, calls the API, and returns structured output. This section covers the exact patterns and rules you must follow.

### 8.1 Critical Script Rules

> [!CAUTION]
> MANDATORY : These rules prevent runtime errors in the Profisee Connect execution environment. Violating any of these rules will cause BadRequest errors or silent failures that are difficult to debug.

| # | Rule | Details |
| --- | --- | --- |
| 1 | Use lowercase property names | Access input.records (not input.Records). Return isSuccess, shouldRetry, error, records (all lowercase). |
| 2 | Use string concatenation | Use "Hello " + name instead of template literals (`Hello ${name}`). Template literals are not supported. |
| 3 | Use indexOf instead of includes | Use array.indexOf(value) >= 0 instead of array.includes(value). The includes method is not available. |
| 4 | Always include retry error codes | Define const retryErrorCodes = [408, 429, 500, 502, 503, 504]; at the top of every script. |
| 5 | fetch is synchronous | Profisee's fetch returns a response object directly. Do not use await, .then(), or async functions. |
| 6 | Parse response body manually | The response body is a string. Use JSON.parse(fetchResponse.body) to convert to an object. |

### 8.2 Script Template (No Authentication)

Use this template for APIs that require no authentication or use an API key in a header:

```
import { fetch } from "Profisee";

const retryErrorCodes = [408, 429, 500, 502, 503, 504];
```

export function execute(input) {

var results = [];

var records = input.records || [];

for (var i = 0; i < records.length; i++) {

var record = records[i];

// Build the request URL

var url = "https://api.example.com/endpoint"

+ "?param=" + encodeURIComponent(record.InputField);

// Make the API call

var fetchResponse = fetch(url, {

method: "GET",

```
headers: {
"Accept": "application/json"
}
});
```

// Handle network exceptions

if (fetchResponse.exceptionType) {

```
return {
```

isSuccess: false,

error: fetchResponse.error || "Network error",

shouldRetry: fetchResponse.shouldRetry || false

```
};
}
```

// Handle HTTP errors

if (!fetchResponse.ok) {

```
return {
```

isSuccess: false,

error: "HTTP " + fetchResponse.status,

shouldRetry: retryErrorCodes.indexOf(

fetchResponse.status) >= 0

```
};
}
```

// Parse the response

var data = null;

try {

data = JSON.parse(fetchResponse.body);

```
} catch (e) {
return {
```

isSuccess: false,

error: "Failed to parse response",

shouldRetry: false

```
};
}
```

// Map API response to output fields

var outputRecord = {

Output1: data.field1 || null,

Output2: data.field2 || null

```
};
```

results.push(outputRecord);

```
}

return {
```

isSuccess: true,

shouldRetry: false,

error: "",

records: results

```
};
}
```

### 8.3 Script Template (OAuth2 Authentication)

Use this template for APIs that use OAuth2 client credentials:

```
import { fetch, getOAuthToken } from "Profisee";

const retryErrorCodes = [408, 429, 500, 502, 503, 504];
```

export function execute(input) {

// Retrieve OAuth token

var oAuthResponse = getOAuthToken(input.authSettings);

if (!oAuthResponse.ok) {

```
return {
```

isSuccess: false,

error: oAuthResponse.error || "Auth failed",

shouldRetry: false

```
};
}
```

var results = [];

var records = input.records || [];

for (var i = 0; i < records.length; i++) {

var record = records[i];

var url = "https://api.example.com/endpoint";

var fetchResponse = fetch(url, {

method: "GET",

```
headers: {
"Authorization": "Bearer "
```

+ oAuthResponse.token,

```
"Accept": "application/json"
}
});
```

// ... same error handling as above ...

```
}

return {
```

isSuccess: true,

shouldRetry: false,

error: "",

records: results

```
};
}
```

### 8.4 Script Template (API Key in Header)

Use this pattern when the API requires an API key in a custom header. The API key is passed as a Service-scope Credential input.

```
import { fetch } from "Profisee";

const retryErrorCodes = [408, 429, 500, 502, 503, 504];
```

export function execute(input) {

var apiKey = input.ApiKey;

var results = [];

var records = input.records || [];

for (var i = 0; i < records.length; i++) {

var record = records[i];

var url = "https://api.example.com/search"

+ "?q=" + encodeURIComponent(record.SearchTerm);

var fetchResponse = fetch(url, {

method: "GET",

```
headers: {
"X-API-Key": apiKey,
"Accept": "application/json"
}
});

// ... error handling ...
}

return {
```

isSuccess: true,

shouldRetry: false,

error: "",

records: results

```
};
}
```

### 8.5 Mapping Array Responses

When an API returns an array of results, flatten them into numbered output fields:

```
// Example: API returns { "results": [ { "name": "...", "score": 0.95 }, ... ] }
```

var results\_array = data.results || [];

var outputRecord = {};

// Capture up to 3 results

for (var j = 0; j < 3; j++) {

var idx = j + 1;

if (j < results\_array.length) {

outputRecord["ResultName" + idx] = results\_array[j].name || null;

outputRecord["ResultScore" + idx] = results\_array[j].score || null;

```
} else {
```

outputRecord["ResultName" + idx] = null;

outputRecord["ResultScore" + idx] = null;

```
}
}
```

## 9. Convert the Script to JSON String

The scriptContent field in the artifact must be a single JSON string with all special characters properly escaped. Follow this process:

* Write and test your script in a plain .js file first.
* Verify the logic is correct by reviewing the code.
* Convert the script to a JSON-escaped string:
* Replace all backslashes (\) with double backslashes (\\)
* Replace all double quotes (") with escaped quotes (\")
* Replace all newlines with \r\n
* Wrap the entire result in