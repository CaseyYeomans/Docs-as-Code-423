# Edit Accounts

You can change account information, assign account permissions, assign roles to accounts, and assign accounts to [teams](https://support.profisee.com/wikis/profiseeplatform/add_teams) using the edit function.

To edit an account:

1. Click **Accounts and Teams** in the navigation panel under Administration.
2. Click **Accounts**.
3. Select the account to edit from the list of accounts.
4. Click **Edit** in the Accounts toolbar.

The Account edit panel opens.
5. On the Generaltab, you can edit the following information:

- **First name**
- **Last name**
- **Description**
- **Email address**

If the information fields contain information imported from Active Directory, any information edited in Accounts will be used instead within the Profisee application.

6. If desired, click **Enable** under Unattended Authentication to generate a unique Client ID.

This setting must be enabled for another program to be able to log in on behalf of this user. If this setting is not enabled, the user can only log in directly through Profisee FastApp Studio.

When submitting any Unattended Authentication request, any permissions required to complete the request (including roles or entity level permissions) should be assigned directly to the user or via teams. You should not assign permissions to this user by Active Directory group membership. Failure to do so may result in failed requests.

7. On the **Roles** tab, you can [assign one or more roles](https://support.profisee.com/wikis/profiseeplatform/assign_user_roles) to an account.

For more information, see [Roles Overview](https://support.profisee.com/wikis/profiseeplatform/roles_overview).

8. On the **Teams** tab, you can add accounts to functional groups.

You must first [create a group under Teams](https://support.profisee.com/wikis/profiseeplatform/add_teams) to populate the list of teams.

To add an account to a team:

1. Select the team in the **Available teams** pane.
2. Click the right arrow to add the role to the **Assigned teams** pane.
9. On the **Permissions** tab, you can [assign account permissions](https://support.profisee.com/wikis/profiseeplatform/assign_permissions).

For more information, see [Permissions Overview](https://support.profisee.com/wikis/profiseeplatform/permissions_overview).
10. Click **Save and Close** to finish editing the account.