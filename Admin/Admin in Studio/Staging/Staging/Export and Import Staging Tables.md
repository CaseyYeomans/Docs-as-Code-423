# Export and Import Staging Tables

Staging Table administration allows administrators the ability to define one or more staging tables to support bulk loading of data into your record data model. Exporting and importing staging table definitions makes these table definitions and related configuration portable across instances of the Profisee Platform.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i57e73dbca8fb605e.png)

## Export Selected Staging Tables

1. In the navigation panel, under Administration, click **Staging Tables**.
2. Select a staging table definition in the list.
3. On the staging tables toolbar, click **Import/Export**.
4. On the menu, click **Export**.
5. When exporting a single table, browse to the desired folder location and select a file name to save the definition.

When exporting multiple tables, browse to the desired folder location.
6. Click **OK**.

The staging table definition file is saved in the selected location with the file extension \*.`stagingtable`.

## Import Selected Staging Tables

1. Connect to the server where you want to deploy the staging table definitions.
2. In the navigation panel, under Administration, click **Staging Tables**.
3. On the staging table edit toolbar, click **Import/Export**.
4. On the menu, click **Import**.
5. Browse to the location where the staging table definition files are saved.
6. Select a definition file to import.
7. Click **Open**.

The imported definition appears in the list.

## See Also

[Command Line Utility Reference for Exporting and Importing](https://support.profisee.com/wikis/profiseeplatform/command_line_utility_reference_for_exporting_and_importing)