# Export and Import Accounts

The Accounts feature area includes the ability to export accounts to file and to import them into the same server, or to a different server. This process provides a way to export account configurations to back up the information or to deploy them to other instances.

Only accounts with the Super Administrator role have the ability to import and export accounts.

## Export Selected Accounts

To export one or more accounts:

1. In the navigation panel, under Administration, click **Accounts and Teams**.
2. Click **Accounts**.
3. Select one or more accounts in the list.
4. In the Accounts toolbar, click **Import/Export**.
5. On the menu, click **Export**.
6. Browse to the file location to save the account files.
7. Enter a name for the file.

- When one account is exported, the file name defaults to the name of the account. You can edit the default name.
- When multiple accounts are exported, the file name defaults to Accounts. You can edit the default name.
8. Click **Save**.

The accounts are saved in the selected location with the file extension \*.accounts.

Multiple accounts are exported to a single file.

Account permissions and roles are included in the exported file.

All accounts are exported with team memberships. You can choose to import them or not when you import the account.

## Export All Accounts

To export all accounts for the current Profisee instance:

1. In the navigation panel, under Administration, click **Accounts and Teams**.
2. Click **Accounts**.
3. Click the row header column header (the empty cell in the heading row) to select all accounts in the grid.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i706dbba7ba3c3996.png)

All accounts are selected.
4. On the Accounts toolbar, click **Import/Export**.
5. On the menu, click **Export**.
6. Browse to the location to save the accounts file.
7. Enter a name for the file.
8. Click **OK**.

The file is saved in the selected location with the specified file name and the extension \*.accounts.

## Import an Account File Without Team Memberships

To import an accounts file:

1. In the navigation panel, under Administration, click **Accounts and Teams**.
2. Click **Accounts**.
3. In the Accounts toolbar, click **Import/Export**.
4. On the menu, click **Import**.
5. Browse to the file location where the files are saved.
6. Select an accounts file to import.

If an account in the file already exists in Profisee, you can choose whether or not to overwrite the existing account.
7. Click **Open**.

The accounts in the file are added to the list.

## Import a Account File With Team Memberships

To import an accounts file maintaining team memberships for the accounts:

1. In the navigation panel, under Administration, click **Accounts and Teams**.
2. Click **Accounts**.
3. In the Accounts toolbar, click **Import/Export**.
4. On the menu, click **Import** with team memberships.
5. Browse to the file location where the files are saved.
6. Select an accounts file to import.

If an account in the file already exists in Profisee, you can choose whether or not to overwrite the existing account.
7. Click **Open**.

The accounts in the file are added to the list of accounts. Any team assignments are re-created.

Current team memberships for existing accounts will be lost when existing accounts are imported without team memberships, but the option to overwrite them is selected.

If accounts in an imported file do not exist in Active Directory on the current system, an error displays and those accounts are omitted from the import.

When accounts are imported with memberships to teams that do not exist in the target environment, the teams are created.

You can only import one accounts file at a time through the application interface. To import multiple accounts files at once, use the Command Line Utility. For more information, see [Command Line Utility Reference for Exporting and Importing](https://support.profisee.com/wikis/profiseeplatform/command_line_utility_reference_for_exporting_and_importing).