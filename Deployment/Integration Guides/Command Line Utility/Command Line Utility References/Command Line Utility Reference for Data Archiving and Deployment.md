# Command Line Utility Reference for Data Archiving and Deployment

Use the Command Line Utility (Profisee.MasterDataMaestro.Utilities.exe) to archive and deploy master data, and import/export archiving strategies.

## Switches

The following switches are available for use for Data Archiving and Deployment with Profisee.MasterDataMaestro.Utilities.exe:

| Option | Description |
| --- | --- |
| /URL:https://serverName/virtualDirectory | Specifies the connection string to use. |
| /CLIENTID:<Client ID value> | This value can be copied from the account enabled for unattended authentication. |
| /ARCHIVEDATA | Archives master data to a file based on the settings in the archive strategy. Requires /FILE and /STRATEGY Optional: /BATCHSIZE and /CORELIMIT |
| /DEPLOYDATA | Deploys the data from an archive file to the system model. Requires /FILE |
| /STRATEGY:strategyName | Specifies the name of the archive strategy to use. Used with /ARCHIVEDATA |
| /FILE:"pathToFile" | Archives or deploys data using the specified file. Requires a valid path to a file or folder. Used with /ARCHIVEDATA and /DEPLOYDATA |
| /CORELIMIT:maxCores | Limits the number of client cores used in the data archiving process. If no limit is specified, then the limit defaults to one core. Optional; used with /ARCHIVEDATA |
| /BATCHSIZE:*numberOfMembers* | The number of members to include in each batch during archiving. Defaults to 1000 members if no batch size is specified. Recommended range is 500 to 10000. Use a lower setting if communication errors occur. Optional; used with /ARCHIVEDATA |

For information on switches to import and export archiving strategies, see [Exporting and importing rules, lists, views and strategies](https://support.profisee.com/wikis/profiseeplatform/command_line_utility_reference_for_exporting_and_importing).

## Examples

Build your own commands using the following examples. Change the italicized text to match the corresponding information on your system.

| Task | CLU Command |
| --- | --- |
| Archive data | /URL:https://serverName/virtualDirectory /STRATEGY:ArchiveStrategy /ARCHIVEDATA /FILE:"c:\folder\ArchiveFile.archive" /CLIENTID:<Client ID value> |
| Deploy an archive | /URL:https://serverName/virtualDirectory /DEPLOYDATA /FILE:"c:\folder\ArchiveFile.archive" /CLIENTID:<Client ID value> |
| Process an archiving strategy with number of cores restricted and batch size defined | /URL:https://serverName/virtualDirectory /STRATEGY:ArchiveStrategy /ARCHIVEDATA /FILE:"c:\folder\ArchiveFile.archive" /CORELIMIT:2 /BATCHSIZE:3000 /CLIENTID:<Client ID value> |