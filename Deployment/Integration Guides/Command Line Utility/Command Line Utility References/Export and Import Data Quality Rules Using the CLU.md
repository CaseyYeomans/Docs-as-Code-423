# Export and Import Data Quality Rules Using the CLU

Administrators can export data quality rules from the system for backup, archive, and propagation of rules between environments.

Unlike importing rules from FastApps Studio, the CLU only uses the **Merge rules** import option. This means that it is not possible to delete rules from the target server when importing rules using the CLU.

Once rules are imported, they take effect and are evaluated immediately when master data changes. However, you should explicitly run rules for the entities affected by the import as rules are not evaluated against the existing data automatically. Refer to Data Quality Rules Evaluation Process and Running Rules on Demand using the CLU for further details.

The following switches apply to export and import of rules using the CLU.

## Switches

| Option | Description |
| --- | --- |
| /URL:https://serverName:port/virtualDirectory | Specifies the Profisee server connection string to use. |
| **/CLIENTID:<Client ID value>** | This value can be copied from the account enabled for unattended authentication. |
| /EXPORT | Exports objects from the Profisee server associated with the /TYPE switch. Requires /TYPE and /FILE switches. Optional /ENTITY switch can target the export to rules from a specific entity. |
| /IMPORT | Import objects from the specified file. Requires /FILE switch. |
| /FILE:"pathToFile" | Specifies the path of the target file when exporting and source file when importing. Required for both /EXPORT and /IMPORT switches. |
| /TYPE:RULES | Specifies the type of object to be exported. For data quality rules, the RULES type must be specified. Required with /EXPORT switch. |
| /ENTITY:entityName | Optional switch to limit the export to only those rules from a specific entity. Optional with /EXPORT and /TYPE:RULES switches. |

##

## Examples

The following examples illustrate how to achieve specific goals using the CLU.

| Task | CLU Command |
| --- | --- |
| Export all rules | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /EXPORT /TYPE:RULES /FILE:"C:\myfolder\allrules.rules" /*CLIENTID:<Client ID value>* |
| Export rules for entity Product | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /EXPORT /TYPE:RULES /FILE:"C:\myfolder\product\_rules.rules" /ENTITY:Product /*CLIENTID**:<Client ID value>* |
| Import rules from file allrules.rules | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /IMPORT /FILE:"C:\myfolder\allrules.rules" /*CLIENTID:<Client ID value>* |
| Import all rules files from a directory | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /IMPORT /FILE:"C:\myfolder" /*CLIENTID:<Client ID value>* |

## See Also

[Export and Import Rules using FastApps Studio](https://support.profisee.com/wikis/profiseeplatform/export_and_import_data_quality_rules_using_fastapps_studio)

[Command Line Utility Reference for Data Quality Rules](https://support.profisee.com/wikis/profiseeplatform/command_line_utility_reference_for_data_quality_rules)