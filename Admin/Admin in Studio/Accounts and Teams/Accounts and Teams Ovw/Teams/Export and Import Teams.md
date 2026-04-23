# Export and Import Teams

The Teams feature area includes the option to export teams and then import them into the same server or other servers, or to save them to file for backup purposes. All exported teams include the accounts who are members of the team along with the assigned roles and permissions. You can choose to import a team with or without account team memberships based on the selected menu option.

Only accounts with the Super Administrator role have the ability to import and export teams.

## Export Selected Teams

Export one or more teams:

1. In the navigation panel, under Administration, click **Accounts and Teams**.
2. Click **Teams**.
3. Select one or more teams in the list.
4. In the Teams toolbar, click **Import/Export**.
5. On the menu, click **Export**.
6. Browse to the file location to save the teams files.
7. Enter a name for the file.

- When one team is exported, the file name defaults to the name of the team. You can edit the default file name.
- When multiple teams are exported, you must enter a file name.
8. Click **Save**.

The teams are saved in the selected location with the file extension \*.teams.

## Export All Teams

To export all teams for the current Profisee instance:

1. In the navigation panel, under Administration, click **Accounts and Teams**.
2. Click the row header column header (the empty cell in the heading row) to select all teams in the grid.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i7f8a136621982b11.png)

All teams are selected.
3. On the Teams toolbar, click **Import/Export**.
4. On the menu, click **Export**.
5. Browse to the location to save the teams file.
6. Enter a name for the file.
7. Click **OK**.

The teams are saved in the selected location with the file name and the extension \*.teams.

Multiple teams are exported to a single file.

## Import a Team File Without Account Memberships

To import a teams file:

1. In the navigation panel, under Administration, click **Accounts and Teams**.
2. Click **Teams**.
3. In the Teams toolbar, click **Import/Export**.
4. On the menu, click **Import**.
5. Browse to the file location where the files are saved.
6. Select a teams file to import.
7. Click **Open**.

The teams are added to the list.
8. Add accounts to the teams.

For more information, see Adding a team.

## Import a Team File With Account Memberships

To import a teams file and include account memberships:

1. In the navigation panel, under Administration, click **Accounts and Teams**.
2. Click **Teams**.
3. In the Teams toolbar, click **Import/Export**.
4. On the menu, click Import with account memberships.
5. Browse to the file location where the files are saved.
6. Select a teams file to import.
7. Click **Open**.

The teams are added to the list.
8. Add accounts to the teams.

For more information, see [Add a Team](https://support.profisee.com/wikis/profiseeplatform/add_teams).

If you attempt to import a team that already exists, an error message displays and the team fails to import.

You can only import one teams file at a time. To import multiple teams files at once, use the Command Line Utility. For more information, see [Command Line Utility Reference for Exporting and Importing](https://support.profisee.com/wikis/profiseeplatform/command_line_utility_reference_for_exporting_and_importing).