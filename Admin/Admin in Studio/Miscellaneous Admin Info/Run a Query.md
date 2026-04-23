# Run a Query

Queries allow an administrator to use SQL Server to extract specific and detailed information from the log files of an application or service. Queries can be used to return information about certain kinds of system messages, messages occurring in specific programs, and much more.

To run a query:

1. Open SQL Server Management Studio and connect to the appropriate server.
2. Drill down on the **Databases** folder.
3. Select Profiseeas your database.
4. Click **New Query**.
5. Enter your desired query. Example queries can be found in the following section.
6. Highlight the query and click **Execute.**

The information is returned via a table within SQL Server containing the following information:

- **ID**: An automatically generated system column that displays the order in which the messages were logged
- **Message**: The message message displayed when the message occurred
- **Level**: The severity of the message. [Read more about logging levels.](https://support.profisee.com/wikis/profiseeplatform/configure_logging_levels)
- **TimeStamp**: The date and time the message was logged
- **Exception**: Additional information about the message. This field will not always be populated.
- **LogEvent**: Includes all the content of the message message, including time stamp, message, warning level.
- **EventType**: The message identifier
- **EventCode**: The optional code that additionally identifies the event
- **AssemblyName**: Displays the application or service that logged the message
- **Assembly/Version**: The version of the application or service that was running when the message occurred
- **SourceContext**: Additional information about the assembly that logged the message
- **EnvironmentUserName**: The user or service that logged the information
- **MachineName**: The name of the machine to which the message was logged

### Regular Column Query Examples

**Return all log messages**
SELECT \*
FROM logging.tSystemLog

**Return counts by Level**
SELECT Level, Count(\*) AS LevelCount
FROM logging.tSystemLog
GROUP BY Level
ORDER BY LevelCount DESC

**Return counts, with subtotals, by Service then level**
SELECT
ISNULL(AssemblyName, 'AssemblyName Total') AS AssemblyName,
ISNULL(Level, 'Level Total') AS Level,
Count(\*) AS LevelCount
FROM logging.tSystemLog
GROUP BY ROLLUP(AssemblyName, Level)

**Return counts, with subtotals, by MachineName, Service, then level**
SELECT
ISNULL(MachineName, 'MachineName Total') AS MachineName,
ISNULL(AssemblyName, 'AssemblyName Total') AS AssemblyName,
ISNULL(Level, 'Level Total') AS Level,
Count(\*) AS LevelCount
FROM logging.tSystemLog
GROUP BY ROLLUP(MachineName, AssemblyName, Level)

**Return a distinct list of services (AssemblyName) that have logs.**
SELECT Distinct(AssemblyName)
FROM logging.tSystemLog

**Search for log messages for a range of time**
SELECT \*
FROM logging.tSystemLog
WHERE TimeStamp BETWEEN '2020-01-28 10:13' AND '2020-01-28 12:00'

**Search for log messages with exception**
SELECT \*
FROM logging.tSystemLog
WHERE Exception IS NOT NULL

SELECT \*
FROM logging.tSystemLog
WHERE Exception IS NOT NULL
AND Exception LIKE '%antiforgery%'

**Search for log messages with certain Level(s)**
SELECT \*
FROM logging.tSystemLog
WHERE Level IN ('Error', 'Warning')

**Search for log messages for a specific service (AssemblyName)**
SELECT \*
FROM logging.tSystemLog
WHERE AssemblyName = 'Profisee.Platform.Attachment.Service.Api'

SELECT \*
FROM logging.tSystemLog
WHERE AssemblyName = 'Profisee.Platform.Auth.Service.Api'

**Search for log messages for a specific computer machine name (MachineName)**
SELECT \*
FROM logging.tSystemLog
WHERE MachineName = '*[Machine Name]*'

**Search for log messages with a specific event type**
Single value
SELECT \*
FROM logging.tSystemLog
WHERE EventType = 'ECD6113A'

Multiple values
SELECT \*
FROM logging.tSystemLog
WHERE EventType IN ('ECD6113A', '8A03324B')

**Search for log messages that contain text**
SELECT \*
FROM logging.tSystemLog
WHERE Message LIKE '%File del%'

### JSON Query Examples

The JSON formatted message is in the LogEvent column. See example JSON messages which the queries below exercise. Note that the content of the samples are for example purpose only and may not represent actual properties logged by the Profisee system.

**JSON SQL Functions**

- JSON\_VALUE(): This function will extract specific scalar values from within the JSON text.
- JSON\_QUERY(): This function allows you to retrieve an object or an array from within the JSON text. Can also use to test for whether a object or array is present in the JSON text.
- OPENJSON: This is a table-valued function that parses JSON text and returns objects and properties from the JSON input as rows and columns.

**Search for log messages with a specific EventType property.**

NOTE: EventType is a separate column in the table so can be searched with that column. This example is intended to demonstrate that all regular columns are also within the JSON message column.

SELECT \*
FROM logging.tSystemLog
WHERE JSON\_VALUE([LogEvent], '$.Properties.EventType') = '35ECF3FE'

**Search for log messages that contains a StrategyId property.**
SELECT \*
FROM logging.tSystemLog
WHERE JSON\_QUERY([LogEvent], '$.Properties.StrategyId') is not null

SELECT \*
FROM logging.tSystemLog
WHERE JSON\_QUERY([LogEvent], '$.Properties.RuleId') is not null

**Returning RuleId.Name in the result**
SELECT l.Id, l.Message, l.TimeStamp, JSON\_VALUE([LogEvent], '$.Properties.RuleId.Name') AS RuleName
FROM logging.tSystemLog l
WHERE JSON\_QUERY([LogEvent], '$.Properties.RuleId') IS NOT NULL

**Search for log messages that contain a StrategyId property.**
SELECT \*
FROM logging.tSystemLog
WHERE JSON\_VALUE([LogEvent], '$.Properties.RuleId.Name') = 'MSRP Rule'

**Search for log messages that contain a StrategyId property and a StrategyId Name of 'NameAddress Match'.**
SELECT \* FROM logging.tSystemLog
WHERE JSON\_QUERY([LogEvent], '$.Properties.StrategyId') is not null -- contains a StrategyId property AND JSON\_VALUE([LogEvent], '$.Properties.StrategyId.Name') = 'NameAddress Match' has a StrategyId Name of 'NameAddress Match'

**Search for log messages that contain MatchingStrategyUid of a specific identifier.**
SELECT \*
FROM logging.tSystemLog
WHERE JSON\_VALUE([LogEvent], '$.Properties.MatchingStrategyUid') = '5a52ed75-f7df-4a2b-83e3-06ac59ab816f'

**Search for log messages that contains a Tags array property.**
SELECT \*
FROM logging.tSystemLog
WHERE JSON\_QUERY([LogEvent], '$.Properties.Tags') is not null

**Search for log messages that contains a Tags array property. Return the Tags as JSON.**
SELECT
Id,
JSON\_QUERY(LogEvent, '$.Properties.Tags') as TagsArray,
JSON\_VALUE(LogEvent, '$.Properties.Tags') as Tags
FROM logging.tSystemLog
WHERE JSON\_QUERY([LogEvent], '$.Properties.Tags') is not null

**Search for log messages that contains a Tags array property. Return the Tags that contain a specific element.**
SELECT
l.\*,
JSON\_QUERY(LogEvent, '$.Properties.Tags') as TagsArray
FROM logging.tSystemLog l
OUTER APPLY OPENJSON(JSON\_QUERY(LogEvent, '$.Properties.Tags')) AS x
WHERE JSON\_QUERY([LogEvent], '$.Properties.Tags') is not null
AND x.value='Matching'

### Basic log message with the standard set of properties.

{
"TimeStamp": "2020-01-28T16:05:26.2246731",
"Level": "Error",
"Message": "Error communicating with Active Directory Domain Controller",
"Exception": "System.DirectoryServices.AccountManagement.PrincipalServerDownException: The server could not be contacted.\r\n ---> System.DirectoryServices.Protocols.LdapException: The LDAP server is unavailable.\r\n at System.DirectoryServices.Protocols.LdapConnection.Connect()\r\n at System.DirectoryServices.Protocols.LdapConnection.SendRequestHelper(DirectoryRequest request, Int32& messageID)\r\n at System.DirectoryServices.Protocols.LdapConnection.SendRequest(DirectoryRequest request, TimeSpan requestTimeout)\r\n at System.DirectoryServices.Protocols.LdapConnection.SendRequest(DirectoryRequest request)\r\n at System.DirectoryServices.AccountManagement.PrincipalContext.ReadServerConfig(String serverName, ServerProperties& properties)\r\n --- End of inner exception stack trace ---\r\n at System.DirectoryServices.AccountManagement.PrincipalContext.ReadServerConfig(String serverName, ServerProperties& properties)\r\n at System.DirectoryServices.AccountManagement.PrincipalContext.DoServerVerifyAndPropRetrieval()\r\n at System.DirectoryServices.AccountManagement.PrincipalContext..ctor(ContextType contextType, String name, String container, ContextOptions options, String userName, String password)\r\n at System.DirectoryServices.AccountManagement.PrincipalContext..ctor(ContextType contextType, String name)\r\n at Profisee.Platform.Auth.Service.Api.GrantValidators.WindowsAuthenticationGrantValidator.ValidateAsync(ExtensionGrantValidationContext context) in D:\\DevOps\\Platform\\Auth\\Service\\Branches\\Main\\Api\\GrantValidators\\WindowsAuthenticationGrantValidator.cs:line 53",
"Properties": {
"SourceContext": "Profisee.Platform.Auth.Service.Api.GrantValidators.WindowsAuthenticationGrantValidator",
"AssemblyName": "Profisee.Platform.Auth.Service.Api",
"AssemblyVersion": "1.0.0.0",
"EnvironmentUserName": "CORP\\*[USER NAME]*$",
"MachineName": "*[MACHINE NAME]*",
"EventType": "35ECF3FE"
}
}

### Log message with an array property (Tags).

{
"TimeStamp": "2020-01-30T09:38:47.6700445",
"Level": "Debug",
"Message": "Process step 1 debug info. Tags [\"SouthEast\", \"Finance\", \"Matching\"]",
"Properties": {
"Tags": [
"SouthEast",
"Finance",
"Matching"
],
"ProcessStep": 1,
"MatchingStrategyUid": "5a52ed75-f7df-4a2b-83e3-06ac59ab816f",
"SourceContext": "MatchingServiceNetCore.MatchingStrategyProcessor",
"AssemblyName": "MatchingServiceNetCore",
"AssemblyVersion": "1.0.0.0",
"EnvironmentUserName": "CORP\\*[User Name]*",
"MachineName": "*[MACHINE NAME]*",
"EventType": "8F043298"
}
}
{
"TimeStamp": "2020-01-30T09:38:47.6759124",
"Level": "Debug",
"Message": "Process step 2 debug info...",
"Properties": {
"ProcessStep": 2,
"MatchingStrategyUid": "5a52ed75-f7df-4a2b-83e3-06ac59ab816f",
"SourceContext": "MatchingServiceNetCore.MatchingStrategyProcessor",
"AssemblyName": "MatchingServiceNetCore",
"AssemblyVersion": "1.0.0.0",
"EnvironmentUserName": "CORP\\*[User Name]*",
"MachineName": "[*MACHINE NAME]*",
"EventType": "438CA592"
}
}
\*/