# Export and Import Data Quality Rules using FastApps Studio

Administrators can export data quality rules from the system for backup, archive, and propagation of rules between environments.

## Export Rules

To export rules from the **Data Quality Rules** administration tab in FastApps Studio, perform the following steps:

1. Click **Import/Export** in the rules administration toolbar.

2. Click **Export** on the dropdown menu. The **Export Rules** dialog window opens.

3. Select the desired entities from the list (multiple selections are possible). Click **Select All** to select all of the entities. Click **Clear All** to clear all of the current selections.

4. Click **OK**. The **Export** file browser dialog window opens.

5. Specify the file name and folder where the **.rules** file will be saved.

6. Browse to the desired folder and specify a name for the rules file, or select an existing file from the folder to overwrite. If you chose a file that exists, you will be prompted to confirm that you want to overwrite the existing file. Click **Yes** to overwrite the file or **No** to cancel the save operation.

7. Click **Save**.

Once the rules have been exported, you can:

- Move the file to a different environment for subsequent import.
- Save the file to an archive as a backup.
- Check the file into a source control system if a more rigorous version control process is being followed (Recommended).

## Import Rules

To import rules from the **Data Quality Rules** administration tab in FastApps Studio, perform the following steps:

1. Click the **Import/Export** in the rules administration toolbar.
2. Click **Import** on the dropdown menu. The **Open** file dialog window opens, defaulted to search for the **\*.rules** file type.
3. Browse local or network file folders for the file you wish to import.
4. Click **Open**. FastApps Studio displays the **Select a publishing option** prompt. There are two publishing options: (1) **Merge rules**, which allows you to add or update rules in the server rules inventory with the rules that are in the import file and (2) **Replace rules**, which deletes all existing rules in the server rules inventory and replaces them with the rules in the import file.
5. Click **Merge rules** or **Replace rules**.
6. Click **OK**. Click **Cancel** to cancel the import. The **Publish Rules to Server** dialog window opens.
7. Review changes before publishing. See [Preview Changes on Rules Import](https://support.profisee.com/wikis/profiseeplatform/preview_changes_on_rules_import) for details.
8. Click **Publish**. Click **Cancel** to stop the import process and reject changes.

The imported rules take effect immediately on import when any subsequent changes to the master data occur. However, rules are not run on existing data unless explicitly requested.

## See Also

[Data Quality Rules Evaluation Process](https://support.profisee.com/wikis/profiseeplatform/data_quality_rules_evaluation_process)

[Run Rules on Demand using FastApps Studio](https://support.profisee.com/wikis/profiseeplatform/run_data_quality_rules_on_demand)

[Command Line Utility Reference for Data Quality Rules](https://support.profisee.com/wikis/profiseeplatform/command_line_utility_reference_for_data_quality_rules)