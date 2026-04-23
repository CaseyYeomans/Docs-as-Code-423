# Command Line Utility Reference for Address Verification

Process and cancel processing of address verification strategies using the CLU.

## Switches

The following switches are available for Address Verification with Profisee.MasterDataMaestro.Utilities.exe:

| **Option** | **Description** |
| --- | --- |
| **/URL:https://****serverName/virtualDirectory** | Specifies the Profisee server connection string to use. |
| **/CLIENTID:<Client ID value>** | This value can be copied from the account enabled for unattended authentication. |
| **/STRATEGY:*****strategyName*** | Specifies the name of the strategy to run. /PROCESSADDRESS is required. |
| **/PROCESSADDRESS** | Processes an address verification strategy. Used with /STRATEGY, it can optionally include the following: /INCLUDELOCATION /INCLUDEMAILING /INCLUDENAME /INCLUDEEMAIL /INCLUDEPHONE If none of the above options are included in the command, then processing defaults to the verification options selected in the strategy. If one or more options are selected, then the other verification options in the saved strategy are ignored. Only options included in the verification strategy can be selected using the command line switches. |
| **/CANCEL** | Cancels the running strategy. /PROCESSADDRESS and /STRATEGY are required |
| **/RECORDSTOINCLUDE:****option** | Defines the records to verify based on the record status. Possible options include: UNVERIFIED UNVERIFIEDCHANGED ALL Defaults to unverified records if a value is not included with the option, or if no option is used. |
| **/INCLUDELOCATION** | Performs location verification. /PROCESSADDRESS and /STRATEGY are required |
| **/INCLUDEMAILING** | Performs Mailing verification. /PROCESSADDRESS and /STRATEGY are required |
| **/INCLUDENAME** | Performs Name parsing. /PROCESSADDRESS and /STRATEGY are required |
| **/INCLUDEEMAIL** | Performs Email verification. /PROCESSADDRESS and /STRATEGY are required |
| **/INCLUDEPHONE** | Performs Phone verification. /PROCESSADDRESS and /STRATEGY are required |

## Examples

Build your own commands based on the following examples. Change the italicized text to match your corresponding system information.

| **Task** | **CLU Command** |
| --- | --- |
| Perform address verification using the default strategy settings | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory/PROCESSADDRESS /STRATEGY:strategyName /CLIENTID:<Client ID value> |
| Cancel running strategy | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory/PROCESSADDRESS /STRATEGY:strategyName/CANCEL/CLIENTID:<Client ID value> |
| Process address verification for all records | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /PROCESSADDRESS /STRATEGY:strategyName/ RECORDSTOINCLUDE:ALL/CLIENTID:<Client ID value> |
| Process address verification for all unverified records | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /PROCESSADDRESS /STRATEGY:strategyName/ RECORDSTOINCLUDE:UNVERIFIED/CLIENTID:<Client ID value> |
| Process address verification for unverified and changed records | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory/PROCESSADDRESS /STRATEGY:strategyName/ RECORDSTOINCLUDE:UNVERIFIEDCHANGED/CLIENTID:<Client ID value> |
| Process address verification for unverified changed records for mailing | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /PROCESSADDRESS /STRATEGY:strategyName/ RECORDSTOINCLUDE:UNVERIFIEDCHANGED /INCLUDEMAILING /CLIENTID:<Client ID value> |
| Process address verification for unverified records for email and phone | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory/PROCESSADDRESS /STRATEGY:strategyName/ INCLUDEEMAIL/INCLUDEPHONE/CLIENTID:<Client ID value> |