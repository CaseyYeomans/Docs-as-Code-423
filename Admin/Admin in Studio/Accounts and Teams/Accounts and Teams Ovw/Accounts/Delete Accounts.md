# Delete Accounts

To delete an account:

1. In the navigation panel under Administration, click **Accounts and Teams**.
2. Click **Accounts**.
3. Select the account you want to remove from Profisee from the list of accounts.
4. Click **Delete**.

A confirmation dialog appears.
5. Click **Yes**.

The account is removed from the list of accounts.

You cannot delete your own account from the list.

Any account that has accessed the system whose account is deleted from Profisee is "soft-deleted." The account can no longer sign in, and is removed from any account lists or features. However, any changes in audit, history, and activity log information related to that account are preserved.

Accounts who have never accessed the system who are deleted are permanently removed.

Role assignments, team assignments, and permissions are permanently removed for all deleted accounts.

If you re-add a soft-deleted account through Profisee, the "Added On" date will display the date when the account was first added.

An account who is statically assigned to one or more workflows is removed from all workflows when the account is deleted from Profisee. No additional action is required.

An account with a dynamic override assignment in one or more workflows who is deleted from Profisee must be manually removed from the workflow code.

There must always be one Super Administrator account in the Profisee instance. You cannot delete the last account with the Super Administrator role, or remove this role from the last account with it assigned.

In the rare event that the last two Super Administrator accounts delete each other simultaneously, rerun Configuration Manager (changing no settings) to re-establish an administrator account.