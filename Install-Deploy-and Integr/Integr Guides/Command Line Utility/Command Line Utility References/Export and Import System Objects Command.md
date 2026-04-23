# Export and Import System Objects Using the Command Line Utility

You can deploy most objects related to a model, including model metadata as well as data quality rules and objects used for Profisee features (such as strategies and applications) using the Command Line Utility (CLU). This process is useful for backing up information as well as for moving application changes between servers.

Exporting and importing all model data and objects is a four-step process:

1. Export the system model metadata and objects (including rules, lists, views, and other model-specific objects).
2. Export the model data using data archiving.
3. Import the model metadata, rules, lists, views, and strategies.
4. Deploy the model data using data deployment.

To export a model object using the Command Line Utility:

| Task | CLU Command |
| --- | --- |
| Export all model objects of all types | /URL:https://serverName/virtualDirectory /EXPORT /TYPE:ALL /FILE:"c:\folder" /CLIENTID:<Client ID value> |
| Archive model data | /URL:https://serverName/virtualDirectory /STRATEGY:archiveStrategy /ARCHIVEDATA /FILE:"c:\folder\archiveFile.archive" /CLIENTID:<Client ID value> |

Exporting all items for the system model appends a time and date stamp to the file names of the exported items.

To deploy a model using the Command Line Utility: CLIENTID:<Client ID value>

| Task | CLU Command |
| --- | --- |
| Import all objects of all types | /URL:https://serverName/virtualDirectory /IMPORT /TYPE:ALL /FILE:"c:\folder" /CLIENTID:<Client ID value> |
| Deploy an archive | /URL:https://serverName/virtualDirectory /DEPLOYDATA /FILE:"c:\folder\archiveFile.archive" /CLIENTID:<Client ID value> |

Model metadata, rules and other objects can be exported through other administrative areas of Profisee. The command line option is often easier to use, however, and useful when you need to perform the same tasks multiple times. There is currently no equivalent within Profisee FastApps Studio for exporting model metadata and associated model objects in a single action. For more information, see [CLU reference for importing and exporting](https://support.profisee.com/wikis/profiseeplatform/command_line_utility_reference_for_exporting_and_importing).