# Accounts Overview

A Profisee Platform **user** or **user account** identifies each user who may access the system. User accounts reference Active Directory identities, as AD is used for authentication of all users.

Open the Users tab under Accounts and Teams to add user accounts to the system, remove users from the system, maintain user properties and assign access to functions and data. You must be a User and Teams Administrator (see Roles) to maintain users. You must be a Permission Administrator to assign permissions to users.

The Profisee Platform uses Active Directory (AD) for authentication, thus each user account in Profisee must reference an existing AD account in Windows Server Active Directory or Azure Active Directory. Specify AD accounts or groups of accounts to import from available Active Directories on the network when adding a user.

If you assign added users to teams, they inherit team roles and permissions once they log in to the Profisee Platform. Creating a team is the easiest way to assign the same access to multiple users. For more information, see the [Teams overview](https://support.profisee.com/wikis/profiseeplatform/teams_overview).

To copy user configurations from one Profisee instance to another, export users to a file and then import the file to the target instance. See [Export and Import Users](https://support.profisee.com/wikis/profiseeplatform/export_and_import_users) for more information.

The Users tab displays the following information:

| | |
| --- | --- |
| Column Name | Description |
| **User Account** | The user's Active Directory account name |
| **Account Type** | Displays whether the account is an Active Directory user or an Active Directory group. |
| **Display Name** | The name displayed for the user in By default, this information is copied from Active Directory, but it can be edited in the Users feature area. |
| **Description** | Optional descriptive text By default, this information is copied from Active Directory, but it can be edited in the Users feature area. |
| **Email Address** | The user's email address By default, this information is copied from Active Directory, but it can be edited in the Users feature area. |
| **Number of Roles** | The total number of roles assigned to a user |
| **Number of Teams** | The total number of teams that include the user as a member |
| **Added On** | The date the user was added |

Group details are not imported from Active Directory groups and must be configured manually.

Users are assigned roles and permissions that define their capabilities in Profisee. For more information, see [Roles Overview](https://support.profisee.com/wikis/profiseeplatform/roles_overview) and [Permissions Overview](https://support.profisee.com/wikis/profiseeplatform/permissions_overview).

The user account entered as the First Administrator during configuration of a new instance is automatically added to the list of users and is assigned the Super Administrator role.

An account must have unattended authentication enabled for another program to be able to log in on its behalf. If this setting is not enabled, the user can only log in directly through Profisee FastApp Studio. This setting can be enabled in the [Edit Account](https://support.profisee.com/wikis/profiseeplatform/edit_accounts) panel. When enabled, a unique Client ID used for authentication is generated for that account.