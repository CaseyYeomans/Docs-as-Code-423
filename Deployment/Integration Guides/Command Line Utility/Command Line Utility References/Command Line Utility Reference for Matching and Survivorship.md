# Command Line Utility Reference for Matching and Survivorship

Use the CLU to execute Matching and Survivorship strategies, and to cancel processing strategies.

As of the 2025.R1 Matching and Survivorship update, it is **highly** **recommended** that all customers use the Profiseee REST API matching microservice instead of the Command Line Utility.

Note that the matching strategy must be enabled before matching can be processed.

## Switches

The following switches are available for use in matching and survivorship strategies with Profisee.MasterDataMaestro.Utilities.exe:

| Option | Description |
| --- | --- |
| /URL:https://serverName/virtualDirectory | Specifies the Profisee server connection string to use. |
| /CLIENTID:<Client ID value> | This value can be copied from the account enabled for unattended authentication. |
| /STRATEGY:strategyName | Specifies the name of the strategy to run. /PROCESSMATCHING or /PROCESSADDRESS required. |
| /PROCESSMATCHING | Processes a matching strategy. /STRATEGY required. |
| /REFRESHINTERVAL:milliseconds | Controls how often processing status is reported. The default interval is 30 seconds. /PROCESSMATCHING required. |
| /INCLUDESURVIVORSHIP | Runs survivorship after the matching process finishes. /PROCESSMATCHING required. |
| /SURVIVORSHIPONLY | Runs only Survivorship without running the matching process. /PROCESSMATCHING required. |
| /CLEARALLPRIORRESULTS | Clears all results from previous matching runs. Disregards filter criteria. /PROCESSMATCHING required. |
| /CLEARMATCHINGRESULTS | Clears matching results without running matching or survivorship. /PROCESSMATCHING **AND** one of these additional clearing options required: /CLEARALLPRIORRESULTS, /CLEARPRIORRESULTS, /CLEARPRIORRESULTSEXCLUDEAPPROVED, /CLEARPRIORRESULTSEXCLUDEUSERMAPPED |
| /CLEARPRIORRESULTS | Clears all previous results for this strategy. Complies with strategy filter criteria. /PROCESSMATCHING and /CLEARALLPRIORRESULTS **OR** /CLEARPRIORRESULTS required. |

## Examples

Build your own commands using the following examples. Change the italicized text to match the corresponding information on your system.

| Task | CLU Command |
| --- | --- |
| Process matching | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/maestro /PROCESSMATCHING /STRATEGY:strategyName /CLIENTID:<Client ID value> |
| Process matching and clear prior matching results | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/maestro /PROCESSMATCHING /STRATEGY:strategyName /CLEARPRIORRESULTS /CLIENTID:<Client ID value> |
| Process matching and clear prior results except user-mapped | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/maestro /PROCESSMATCHING /STRATEGY:strategyName /CLEARPRIORRESULTS /CLEARPRIORRESULTSEXCLUDEUSERMAPPED /CLIENTID:<Client ID value> |
| Process matching and clear prior results except approved | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /PROCESSMATCHING /STRATEGY:strategyName /CLEARPRIORRESULTS /CLEARPRIORRESULTSEXCLUDEAPPROVED /CLIENTID:<Client ID value> |
| Process matching and clear prior results except user-mapped and approved | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /PROCESSMATCHING /STRATEGY:strategyName /CLEARPRIORRESULTS /CLEARPRIORRESULTSEXCLUDEUSERMAPPED /CLEARPRIORRESULTSEXCLUDEAPPROVED /CLIENTID:<Client ID value> |
| Process matching and survivorship | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /PROCESSMATCHING /STRATEGY:strategyName /INCLUDESURVIVORSHIP /CLIENTID:<Client ID value> |
| Process survivorship only | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /PROCESSMATCHING /STRATEGY:strategyName /SURVIVORSHIPONLY /CLIENTID:<Client ID value> |
| Cancel the running strategy | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /PROCESSMATCHING /STRATEGY:strategyName /CANCEL /CLIENTID:<Client ID value> |
| Rebuild the matching index for a strategy | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /PROCESSMATCHING /STRATEGY:strategyName /INDEXFULLREBUILD /CLIENTID:<Client ID value> |
| Rebuild the matching index for a strategy without running the strategy | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /PROCESSMATCHING /STRATEGY:strategyName /INDEXFULLREBUILD /INDEXONLY /CLIENTID:<Client ID value> |
| Unload the matching index for a strategy | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /PROCESSMATCHING /STRATEGY:strategyName /INDEXUNLOAD /INDEXONLY /CLIENTID:<Client ID value> |