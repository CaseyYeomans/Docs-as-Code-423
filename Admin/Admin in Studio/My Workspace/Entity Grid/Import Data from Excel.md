# Import Data from Excel

To import data into an entity from an Excel spreadsheet:

1. With the entity open that you want to import data into, click **Import** on the entity grid toolbar.

The Import Data dialog appears. The Excel option is selected by default.
2. Click **Open**.
3. Browse for and select the Excel file in the dialog, and then click **Open**.
4. In Import Data dialog, select the range of data in the **Range** list and then click **Preview**.
5. View the preview data to ensure that you selected the correct range, and then click **Next**.
6. Select the attribute that corresponds with the data in the first column by clicking the menu at the top of the column. This maps the data to the correct attribute.
7. Map the rest of the columns to the correct attributes using the column menus. Suggestions from Profisee appear by default. Map any columns that you do not want to import to **<Ignore>**.
8. When all of the columns have been mapped, click **Finish**.

The Excel data is imported into the current grid view.

You may need to install data access drivers to import data from Excel, especially when Excel was installed using Office 365. Refer to the Profisee support portal for a workaround.

Selecting the **Preview records before publishing** option at the bottom of the Import Data dialog defers publishing of imported records. This option is selected by default.

Selecting the **Automatically add domain values** option at the bottom of the Import Data dialog automatically adds any new values from your imported data to Profisee source entities for DBAs. This option is selected by default. Always select this option when you plan to import new DBA values; otherwise, new values will be discarded.

Create new, free-form text attributes for all unmapped attributes in the Import Data dialog by clicking **Create new attributes** during the column mapping step.

You can discard your mapping information by clicking **Back** in the Edit Column Mappings step. When asked to confirm discarding mappings, click **Yes**.

- You cannot import data values from Excel into attributes which are restricted in Profisee.

- To replace values in an entity grid with blank values in an excel file, you must deselect the **Preview** option.

### See More

- [Troubleshoot Importing Data from Excel](https://support.profisee.com/wikis/profiseeplatform/troubleshoot_importing_data_from_excel)