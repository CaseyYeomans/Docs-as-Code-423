# Deployment & CI/CD

# Best Practices for Deployment

---

Solution deployment refers to the process of taking application components and making them available for use by the business. It is the implementation step where the solution moves from development and testing phases into real-world operation. Deployment is essential because a solution is only valuable when it is accessible to end users or operational systems. Deployment ensures the solution is live and functional in the environment where needed.Not to be confused with software deployment (installation), this guide describes the processes for deploying Profisee solutions from one environment to another (also sometimes referred to as migration). This guide describes the Profisee Platform deployment concepts and enables you to create deployment processes for your MDM solutions.

### Key Principles for Success

* Recoverability: Backup your target systems before deployment. Deployments are time-sensitive and failure can have a major impact on the business. You must ensure that recovery is an option.
* Security: Review and apply Profisee’s Best Practices for Security to ensure that permissions are appropriate for the project team roles.
* Change Management: Change control processes that are standardized and automated to the greatest degree possible reduce the risk of human error and improving repeatability.
* Continuous Integration and Deployment (CI/CD): The concepts and features described in this document can be used to support your CI/CD operations.

### Solution Deployment

* Solution deployments consist of creating portable definition files for the components of an application (e.g., the model metadata, matching strategies, AV rules, etc.).
* In addition to the Profisee artifacts deployment involves configuring infrastructure so the solution can manage production workloads and be accessed securely by the users and other systems.
* There are exceptions, but it generally is possible for a newer version of Profisee to import objects from an older version. We recommend upgrading target instances to the same version as the source instance before deploying solution objects.
* You can export and import Profisee artifacts into the file system. This enables you to use a local repository with your preferred source code software (e.g. Azure DevOps and GitHub).
* When migrating from PaaS to SaaS, the objective is to ‘lift and shift’ your complete solution from a source instance to a target instance. In this case it is appropriate to backup and then restore the database repository and the file repositories to the target server. Contact Technical Support for guidance on how to perform these actions.
* In future releases we will deliver solution deployment features in Portal and the REST API rather than the CLU.

#### Key Concept: Data Deployment (aka Data Migration)

* MDM data is the data under management in your MDM applications. MDM data is not generally transferred between environments in production in the ways that the other solution components are. For example, your production Profisee Customer data should by synchronized with your CRM and other operational systems in production. The production identifiers need to match across that environment. We have seen customers attempt to persist Cluster IDs or Golden Record codes across environments (dev/test/prod), but this requires significant effort. Instead, we recommend keeping each environment internally consistent using extract, transform, and load techniques (ELT or ETL).
* However, for specific use cases like updating reference data, or first-time data loading, and for smaller data volumes under a million records, it can be appropriate to deploy data between Profisee environments. The Profisee Platform has multiple mechanisms for loading data. For ad-hoc, manual data deployments customers typically use the Data Archiving feature or the Excel download and import capability.
* File attachments can be copied between environments if GUIDs for the entities and the records are the same.

#### Key Concept: GUIDs

Profisee uniquely identifies application objects using GUIDs (Global Unique Identifiers). In this context an object may be a model, entity, attribute, rule, strategy, view, application, etc. \*\*\_Maintaining the same GUID for the same object across environments is imperative for successful deployment and ongoing maintenance.\_\*\*\_ \_

When deploying objects Profisee uses the GUID of an object first, and then the Name, to determine if it is the same object. If an object has a different name between environments but has the same GUID, Profisee considers these equivalent from an identity standpoint. Using internal GUIDs supports name changes for objects and preserves referential integrity between objects. Avoid creating conflicting GUIDs between environments wherever possible.

* Do not create objects (e.g., an entity or an attribute) in a production environment after creating them in a test or development environment. While the objects may share the same name and context, they are not considered the same because the GUIDs are different, and this difference will cause a conflict during future deployments.
* Do not use the “Copy to New” action in Advanced Modeling prior to saving a model file and deploying it to another environment. “Copy to New” is for the sole purpose of creating a replica model, while a distinctly different model, in the same environment. Use this action only for its intended purpose.

#### Application Interfaces

Refer to [Feature Compatibility by Version](https://support.profisee.com/wikis/release_notes/version_compatibility_by_version) for the latest information on which application interfaces support the components and artifacts you are working with.  As a reminder:

* SaaS customers cannot access or use database tables or views.
* Reports are developed using external tools like Power BI.
* Data archival files are for small data volumes only.
* Data archives do not contain record history or file attachments.
* Workflow development requires Visual Studio.
* The CLU deploys Accounts & Teams, but not the security assignments & permissions, since each environment is expected to require different permissions.

#### Manual Deployment

* Administrators can manually export and import solution components in the Profisee Portal or FastApp Studio interfaces.
* You should always check-in and check-out the files into a source code control system (e.g. GitHub or Azure DevOps) to coordinate and audit changes.

#### REST API

* Profisee’s REST API is an OpenAPI service that provides advanced users with programmatic access to the MDM metadata, data, and operations within the Profisee platform.
* The API supports OData specifications, including features like paging, filtering, and sorting. The APIs use JSON media types for requests and responses.
* The REST API is installed automatically with the Profisee Platform and requires no additional configuration. You can access the API by navigating to your Profisee service URL followed by "/rest", which directs you to the API documentation page.
* Deployments can be implemented using scripts that utilize the REST API endpoints.
* Import the OpenAPI JSON directly into Postman to develop and test your automation processes.
* Authentication requires a Client ID (x-api-key), which can be managed in the Accounts and Teams administration section.   Be extremely cautious when saving Client IDs in your scripts.

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
# 5 Right click the file and “Run with PowerShell"
# ------------------------------------------------------------------------------------------------

# ---------- Configuration ----------
$SourceUrl    = "https://profiseecloud.com/dev"
$SourceApiKey = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"

$TargetUrl    = "https://profiseecloud.com/test"
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
        "Accept"    = "application/json"
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
#            Default behavior will migrate ALL rules but you can modify this to filter the rules to migrate (examples below)
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

$jsonBody = ConvertTo-Json -InputObject @($detailedRules) -Depth 20

Write-Host "`nSending rules to target environment '$TargetEnv'..." -ForegroundColor Yellow -NoNewline

try {
    Invoke-RestMethod `
        -Uri $TargetUrl `
        -Method PUT `
        -Headers $targetHeaders `
        -Body $jsonBody

    # optional - display jsonbody on console
    #Write-Host "$jsonBody" -ForegroundColor Blue

    Write-Host "Rules successfully updated in target environment '$TargetEnv'." -ForegroundColor Green
}
catch {
    Write-Host "Failed to update rules in '$TargetEnv'." -ForegroundColor Red
    Write-Host $_.Exception.Message

    if ($_.Exception.Response) {
        $reader = New-Object System.IO.StreamReader($_.Exception.Response.GetResponseStream())
        Write-Host $reader.ReadToEnd()
    }
}
```

#### Command Line Utility (CLU)

* Profisee’s CLU (also known as Profisee Platform Tools) provides a command line interface for solution deployments in addition to other operations. CLU commands can be issued interactively, or in a script, which helps to standardize deployment activities.
* A complete reference for the CLU is included in the [Platform Help](https://support.profisee.com/wikis/profiseeplatform/export_and_import_system_objects_using_the_command_line_utility) and examples are listed below.
* The CLU requires a valid Client ID (see the Help topic on [unattended authentication](https://support.profisee.com/wikis/profiseeplatform/edit_accounts)). Be extremely cautious when saving Client IDs in your scripts.
* The CLU was originally designed for customers using On-Premise/IaaS infrastructure. Customers on all infrastructure types can use it, but it requires a Windows VM or application server to operate as a client of the Profisee instance.
* As the Profisee Platform features migrate from FastApp Studio/CLU to the Profisee Portal/REST API customers will need to have both CLU and REST API processes. Eventually, the CLU will be deprecated.

#### CLU Troubleshooting Conflicts and Correcting Issues

* The CLU can create and update objects but cannot delete them. Removing unused objects requires manual intervention.
* Deploying model updates may also generate errors and require manual confirmation of the changes. If conflicting model changes exist (e.g., a name collision), use Profisee FastApp Studio to deploy the model metadata and resolve the conflicts.
* The CLU is for unattended automation and will log problems that need to be resolved by an administrator. Your batch file should capture the CLU output to a text file so that the deployment can be verified. If strategies or other elements are imported with reference errors, open these items in Profisee FastApp Studio after the import, correct the issues and save the object.
* Hierarchies and Matching strategies can have circular dependencies with Forms. Perform the imports a second time to resolve the missing objects.

#### Exporting with the CLU

* Use the export command to create a portable definition file for deployment. Commands can be included in a batch script for exporting multiple object types. The following is a sample command for exporting the solution objects supported by the CLU.
* Save the example to a \*.bat file and replace the highlighted text with values for your environment.
* Create an empty file folder to receive the set of exported files and use that path in the FILE parameter. You can then run the bat file to export all objects to a set of files in the chosen folder.

```
REM Change to the appropriate CLU directory location for the correct Maestro version.

C:

cd C:\\Program Files\\Profisee\\Master Data Maestro Utilities\\`4.0.4`

REM Export all object types.

Profisee.MasterDataMaestro.Utilities.exe /URL:net.tcp://`_yourserver/yourapp_`/service.svc/tcp `/EXPORT` /TYPE:ALL /MODEL:`_yourmodel_` /FILE:”`_yourdirectorypath_`” /CLIENTID:`_yourclientID_`

Deploying with the CLU
```

* Use the import command to read previously exported object definition files and create/overwrite objects in a target instance. The following is a sample command for importing all Profisee application elements from a file directory.
* Save the example to a \*.bat file and replace the highlighted text with values for your environment.
* Place the previously exported object definition files in a single file folder. You can then run the bat file to import all elements from all files found in the folder.

```
REM Change to the appropriate CLU directory location for the correct Maestro version.

c:

cd C:\\Program Files\\Profisee\\Master Data Maestro Utilities\\`4.0.4`

REM Import all objects found in path.

Profisee.MasterDataMaestro.Utilities.exe /URL:net.tcp://`_yourserver/yourapp_`/service.svc/tcp /IMPORT /FILE:"`_yourdirectorypath_`" /CLIENTID:`yourclientID`
```

#### Archiving Data with the CLU

* The following is a sample command for exporting a data archive file with the CLU.
* Data archives do not contain file attachments, history values, or metadata values (create, update user and datetimes).
* The work to process archive file is performed with client computer resources and so is significantly slower than ETL or REST API. We recommend using the REST API for data volumes over 500,000 records.

```
REM Change to the appropriate CLU directory location for the correct Maestro version.

c:

cd C:\\Program Files\\Profisee\\Master Data Maestro Utilities\\`4.0.4`

REM Archive data to a file using a selected archive strategy definition.

Profisee.MasterDataMaestro.Utilities.exe /URL:net.tcp://`_yourserver_/_yourapp_`/service.svc/tcp /ARCHIVEDATA /STRATEGY:`_yourstrategy_` /FILE:"`_yourdirectorypath_`\\`_filename_`.archive" /CLIENTID:`yourclientID`
```

#### Deploying Data with the CLU

* The following is a sample command for deploying a data archive file.

```
REM Change to the appropriate CLU directory location for the correct Maestro version.

c:

cd C:\\Program Files\\Profisee\\Master Data Maestro Utilities\\`4.0.4`

REM Deploy data from an archive file.

Profisee.MasterDataMaestro.Utilities.exe /URL:net.tcp://`_yourserver_/_yourapp_`/service.svc/tcp /DEPLOYDATA /FILE:"`_yourdirectorypath_`\\`_filename_`.archive" /CLIENTID:`yourclientID`
```

### Deployment Checklist

This template lists the common activities and deliverables for solution deployment – customize it for your project as needed.

| Completed | Task | Responsible Party |
| --- | --- | --- |
| ☐ | Prepare deployment manifest and communication plan |  |
| ☐ | Prepare target system environment resources & settings |  |
| ☐ | Export files |  |
| ☐ | Export application files |  |
| ☐ | Save files in a change tracking or source control system |  |
| ☐ | Archive selected reference data |  |
| ☐ | Back up target Profisee database |  |
| ☐ | Deploy into target environment |  |
| ☐ | Delete metadata elements to be removed from target |  |
| ☐ | Deploy application files to target |  |
| ☐ | Deploy or ETL data to target |  |
| ☐ | Perform manual activities |  |
| ☐ | Create new security groups |  |
| ☐ | Assign or update group permissions |  |
| ☐ | Test deployment |  |
| ☐ | Update release notes and/or system logs |  |