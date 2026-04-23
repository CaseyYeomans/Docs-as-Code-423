# Command Line Utility Reference for Data Quality Rules

The data quality rules engine runs against member data when it is created or updated. However, rules added or changed by an administrator are not run immediately and must be explicitly requested to run in order to re-evaluate the entity against the new, updated, and deleted rules.

Rules hosted in Profisee Portal cannot be run using the Command Line Utility. If you wish to run rules asynchronously, you must use the Profisee REST API.

## Switches

To run data quality rules explicitly using the CLU, use the following switches on Profisee.MasterDataMaestro.Utilities.exe:

| Option | Description |
| --- | --- |
| /URL:https://serverName:port/virtualDirectory | Specified the Profisee server connection string to use. |
| /CLIENTID:<Client ID value> | This value can be copied from the account enabled for unattended authentication. |
| /RUNRULES | Specifies the desire to run data quality rules. Used with /ENTITY. |
| /ENTITY:entityName | Optional switch that specifies the entity for which rules should be run. If omitted, then rules are run for all entities for which rules have been defined. |

## Examples

The following examples show use of the command line to perform rule evaluation tasks:

| Task | CLU Command |
| --- | --- |
| Run rules for all entities | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /RUNRULES /CLIENTID:<Client ID value> |
| Run rules for a specific entity | Profisee.MasterDataMaestro.Utilities.exe /URL:https://serverName/virtualDirectory /RUNRULES /ENTITY:Customer /CLIENTID:<Client ID value> |

If you run rules for all entities, only entities with defined rules are evaluated. The evaluation occurs regardless of whether the Last Evaluated On time is before the Last Rule Changed On time.

## See Also

[Run Rules on Demand using FastApps Studio](https://support.profisee.com/wikis/profiseeplatform/run_data_quality_rules_on_demand)

[Data Quality Rules Evaluation Process](https://support.profisee.com/wikis/profiseeplatform/data_quality_rules_evaluation_process)

[Export and Import Rules using the CLU](https://support.profisee.com/wikis/profiseeplatform/export_and_import_data_quality_rules_using_the_clu)