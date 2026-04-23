# Best Practices for Deployment

Solution deployment refers to the process of taking application components and making them available for use by the business. It is the implementation step where the solution moves from development and testing phases into real-world operation. Deployment is essential because a solution is only valuable when it is accessible to end users or operational systems. Deployment ensures the solution is live and functional in the environment where needed.Not to be confused with software deployment (installation), this guide describes the processes for deploying Profisee solutions from one environment to another (also sometimes referred to as migration). This guide describes the Profisee Platform deployment concepts and enables you to create deployment processes for your MDM solutions.

### Key Principles for Success

- Recoverability: Backup your target systems before deployment. Deployments are time-sensitive and failure can have a major impact on the business. You must ensure that recovery is an option.
- Security: Review and apply Profisee's Best Practices for Security to ensure that permissions are appropriate for the project team roles.
- Change Management: Change control processes that are standardized and automated to the greatest degree possible reduce the risk of human error and improving repeatability.

### Solution Deployment

- Solution deployments consist of creating portable definition files for the components of an application (e.g., the model metadata, matching strategies, AV rules, etc.).
- In addition to the Profisee artifacts deployment involves configuring infrastructure so the solution can manage production workloads and be accessed securely by the users and other systems.
- There are exceptions, but it generally is possible for a newer version of Profisee to import objects from an older version. We recommend upgrading target instances to the same version as the source instance before deploying solution objects.
- You can export and import Profisee artifacts into the file system. This enables you to use a local repository with your preferred source code software (e.g. Azure DevOps and GitHub).
- When migrating from PaaS to SaaS, the objective is to 'lift and shift' your complete solution from a source instance to a target instance. In this case it is appropriate to backup and then restore the database repository and the file repositories to the target server. Contact Technical Support for guidance on how to perform these actions.
- In future releases we will deliver solution deployment features in Portal and the REST API rather than the CLU.

#### Key Concept: Data Deployment (aka Data Migration)

- MDM data is the data under management in your MDM applications. MDM data is not generally transferred between environments in production in the ways that the other solution components are. For example, your production Profisee Customer data should by synchronized with your CRM and other operational systems in production. The production identifiers need to match across that environment. We have seen customers attempt to persist Cluster IDs or Golden Record codes across environments (dev/test/prod), but this requires significant effort. Instead, we recommend keeping each environment internally consistent using extract, transform, and load techniques (ELT or ETL).
- However, for specific use cases like updating reference data, or first-time data loading, and for smaller data volumes under a million records, it can be appropriate to deploy data between Profisee environments. The Profisee Platform has multiple mechanisms for loading data. For ad-hoc, manual data deployments customers typically use the Data Archiving feature or the Excel download and import capability.
- File attachments can be copied between environments if GUIDs for the entities and the records are the same.

#### Key Concept: GUIDs

Profisee uniquely identifies application objects using GUIDs (Global Unique Identifiers). In this context an object may be a model, entity, attribute, rule, strategy, view, application, etc. \*\*\_Maintaining the same GUID for the same object across environments is imperative for successful deployment and ongoing maintenance.\_\*\*\_ \_

When deploying objects Profisee uses the GUID of an object first, and then the Name, to determine if it is the same object. If an object has a different name between environments but has the same GUID, Profisee considers these equivalent from an identity standpoint. Using internal GUIDs supports name changes for objects and preserves referential integrity between objects. Avoid creating conflicting GUIDs between environments wherever possible.

- Do not create objects (e.g., an entity or an attribute) in a production environment after creating them in a test or development environment. While the objects may share the same name and context, they are not considered the same because the GUIDs are different, and this difference will cause a conflict during future deployments.
- Do not use the "Copy to New" action in Advanced Modeling prior to saving a model file and deploying it to another environment. "Copy to New" is for the sole purpose of creating a replica model, while a distinctly different model, in the same environment. Use this action only for its intended purpose.

#### Application Interfaces

| | **Manual** | | **Automation** | |
| --- | --- | --- | --- | --- |
| **Object Type** | **Profisee Portal** | **FastApp Studio** | **REST API** | **Command Line Utility** |
| Model | Yes | Yes | Yes | Yes |
| Data Quality Rules | Yes | No | Yes | No |
| Matching Strategies | No | Yes | Yes | Yes |
| Synonym Lists | No | Yes | Yes | Yes |
| AV Strategies | No | Yes | No | Yes |
| Event Scenarios | No | Yes | No | Yes |
| Desktop Settings (Studio) | No | Yes | No | No |
| System Settings | No | Yes | No | No |
| Web.Config | No | No | No | No |
| Real-Time Eventing | No | Yes | No | Yes |
| External Systems List | No | Yes | No | Yes |
| Data Archival Strategies \*3 \*4 | No | Yes | No | Yes |
| Staging Tables \*1 | No | Yes | No | Yes |
| Subscription Views \*1 | No | No | No | No |
| FastApps (Portal Applications) | No | Yes | No | Yes |
| Reports \*2 | No | No | No | No |
| Forms | No | Yes | No | Yes |
| Hierarchies | No | Yes | No | Yes |
| Presentation Views | Yes | Yes | No | Yes |
| Workflows \*5 | No | Yes | Partial | Yes |
| Accounts & Teams \*6 | No | Yes | No | Partial |
| Cluster Servers | No | Yes | No | Yes |

\*1 SaaS customers cannot access or use database objects

\*2 Reports are developed in external tools like Power BI

\*3 Data archival files are for small data volumes only

\*4 Data archives do not contain record history or file attachments

\*5 Requires Visual Studio

\*6 Accounts & Teams are deployed but security assignments & permissions are not

#### Manual Deployment

- Administrators can manually export and import solution components in the Profisee Portal or FastApp Studio interfaces.
- You should always check-in and check-out the files into a source code control system (e.g. GitHub or Azure DevOps) to coordinate and audit changes.

#### REST API

- Profisee's REST API is an OpenAPI service that provides advanced users with programmatic access to the MDM metadata, data, and operations within the Profisee platform.
- The API supports OData specifications, including features like paging, filtering, and sorting. The APIs use JSON media types for requests and responses.
- The REST API is installed automatically with the Profisee Platform and requires no additional configuration. You can access the API by navigating to your Profisee service URL followed by "/rest", which directs you to the API documentation page.
- Deployments can be implemented using scripts that utilize the REST API endpoints.
- Import the OpenAPI JSON directly into Postman to develop and test your automation processes.
- Authentication requires a Client ID (x-api-key), which can be managed in the Accounts and Teams administration section. Be extremely cautious when saving Client IDs in your scripts.

#### Deploying with the REST API

```
# ------------------------------------------------------------------------------------------------
# Script to programmatically migrate rules from a source instance of Profisee to a target instance
# This emulates some of the functionality previously included in the CLU
# Use at your own risk - this is a prototype - it has limited error handling and minimal functionality
# You may need to set your ExecutionPolicy to RemoteSigned in order to execute a local script
# Tested with 25.4 version - the APIs it uses do not exist in 25.3 or earlier versions
# ------------------------------------------------------------------------------------------------

# ------------------------------------------------------------------------------------------------
# 1 Open the script in any text editing tool
# 2 Set the source and target environment details in the configuration section
# 3 Set the SourceFilter value as needed
# 4 Save the file
# 5 Right click the file and "Run with PowerShell"
# ------------------------------------------------------------------------------------------------

# ---------- Configuration ----------
$SourceUrl = "https://profiseecloud.com/dev"
$SourceApiKey = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"

$TargetUrl = "https://profiseecloud.com/test"
$TargetApiKey = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"

# ---------- Helper: URL Encoding ----------
function Encode-Url {
param (
[Parameter(Mandatory = $true)]
[string]$InputString
)

# Use .NET's built-in URL encoding for full compliance
return [System.Web.HttpUtility]::UrlEncode($InputString).replace("+", "%20")
}

# ---------- Helper: Headers ----------
function Get-Headers {
param ([string]$ApiKey)
return @{
"x-api-key" = $ApiKey
"Accept" = "application/json"
}
}

# ---------- Helper: Extract Environment Name ----------
function Get-EnvironmentName {
param ([string]$Url)
try {
$uri = [System.Uri]$Url
foreach ($seg in ($uri.AbsolutePath -split '/')) {
if ($seg -ne '') { return $seg }
}
return $Url
}
catch {
return $Url
}
}

# ---------- Helper: Normalize URL ----------
function Normalize-Url {
param ([string]$Url)
if ($Url.EndsWith("/")) {
$Url = $Url.Substring(0, $Url.Length - 1)
}
return "$Url/rest/v1/Rules"
}

# ---------- Optional OData filter -----------
# Default behavior will migrate ALL rules but you can modify this to filter the rules to migrate (examples below)
$SourceFilter = ""

# Created datetime
#$SourceFilter = "[`$EnterDTM] ge 2025-12-30T15:38:00"

# Specific entities
#$SourceFilter = "[Entity] IN ('Entity1', 'Entity2', 'Entity3')"

# Specific entity and attribute
$SourceFilter = "[Entity] eq 'Account' AND [Attribute] eq 'Industry'"
#$SourceFilter = "%5BEntity%5D%20eq%20%27Account%27%20AND%20%5BAttribute%5D%20eq%20%27Industry%27"
#$SourceFilter = "[Entity] eq 'Account' AND ([Attribute] eq 'Industry' OR [Attribute] eq 'Fiscal Year')"

# prepare the URL encoded filter for use
$SourceFilterEncoded = Encode-Url $SourceFilter
#Write-Host $SourceFilterEncoded
$SourceFilter = $SourceFilterEncoded

# ---------- Normalize the URLs ----------
$SourceUrl = Normalize-Url -Url $SourceUrl
$TargetUrl = Normalize-Url -Url $TargetUrl

$SourceEnv = Get-EnvironmentName -Url $SourceUrl
$TargetEnv = Get-EnvironmentName -Url $TargetUrl

# ---------- STEP 1: GET the rules from source environment ------------
$sourceHeaders = Get-Headers -ApiKey $SourceApiKey
Write-Host "Fetching rules from source environment '$SourceEnv'..." -ForegroundColor Yellow

$allRulesResponse = Invoke-RestMethod `
-Uri "$SourceUrl/?Filter=$($SourceFilter)" `
-Method GET `
-Headers $sourceHeaders

$rules = @($allRulesResponse.data)

if ($rules.Count -eq 0) {
Write-Host "No rules found in source environment '$SourceEnv'." -ForegroundColor Red
return
}

Write-Host "Found $($rules.Count) rule(s) in '$SourceEnv'" -ForegroundColor Green

# ---------- STEP 2: GET rule details ----------
$detailedRules = @()
foreach ($rule in $rules) {
$ruleDetail = Invoke-RestMethod `
-Uri "$SourceUrl/$($rule.id)" `
-Method GET `
-Headers $sourceHeaders

if ($null -ne $ruleDetail) {
$detailedRules += $ruleDetail
}
}

Write-Host "Fetched $($detailedRules.Count) rule(s) from '$SourceEnv'" -ForegroundColor Green

# ---------- STEP 3: PUT the rules to the target environment ----------
$targetHeaders = Get-Headers -ApiKey $TargetApiKey
$targetHeaders["Content-Type"] = "application/json"

$jsonBody = ConvertTo-Js
```