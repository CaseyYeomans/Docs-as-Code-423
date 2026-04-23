# Add Accounts

Add one or more accounts to Profisee from Active Directory:

1. In the navigation panel under Administration, click **Accounts and Teams**.
2. Click **Accounts**.
3. In the Accounts toolbar, click **New**. The **Add users** window opens.
4. In the **Active Directory user or group accounts** free-text field, enter one or more Active Directory account names, group names, or a combination of the two. Use the standard Active Directory format: domain\account or group name.

Separate multiple entries using semicolons (;) or commas (,) between the names.

Active Directory groups are added as new accounts. You can assign permissions to an AD group, or assign the AD group to a team to grant it the effective permissions of that team. When an account in an AD group connects to Profisee for the first time, that account receives the effective permissions of the group and is added as an account.

If an account is removed from an AD group, that account will not retain the effective group permissions, but will retain their directly assigned account permissions.

5. Click **Save**.

The users appear in the list of accounts. The following account information is sourced from AD when the account is added:

- SID (not displayed)
- Display name
- Description
- Email address

Account can be added from multiple Windows Server or Azure Active Directory domains when the domain controller is properly configured to support multiple domains.

Group membership is refreshed based on a timer controlled by the **User cache interval timer** system setting, which is set to 60 minutes by default. To manually refresh membership, click **Refresh Cache**.

The Profisee server must be able to connect to the source AD domains.