# Roles Overview

A Role enables a set of functional capabilities when assigned to an Account or Team. The Profisee Platform contains a predefined list of roles for assignment.

Assign roles to accounts ( see [Accounts overview](https://support.profisee.com/wikis/profiseeplatform/accounts_overview)) and teams (see [Teams overview](https://support.profisee.com/wikis/profiseeplatform/teams_overview)) to define access to feature areas, and to authorize specific functions. Role selection is available through the Roles tab in either Accounts or Teams.

The following roles are available:

| This role: | Allows the account to: |
| --- | --- |
| Address Verification Administrator | - Maintain and execute address verification strategies on entities where the account also has Administration permission - Perform interactive address verification from the entity grid The Address Verification Administrator must also have the System Administrator role to create attributes within the Address Verification feature area. |
| Address Verification Account | - Perform interactive address verification on entities (where the account also has sufficient model access permissions) |
| Batch Integration Administrator | - Manage and process staging table definitions through the Staging Tables feature area |
| Data Archive Administrator | - Maintain and execute data archiving strategies - Deploy data from a data archive - Deploy data on entities where the Data Archive Administrator has Administrator permission assigned The System Administrator role is also required to create new attributes in the context of data deployment. The Data Archive Administrator can see all model metadata but must have separate permissions to view or edit data. Some data may be skipped during deployment if an administrator deploys a data archive created by another administrator with broader data permissions. |
| Event Administrator | - Maintain events for entities where Administrator permission is assigned - Register subscribers - Maintain subscriber configurations - Maintain the external systems list |
| Matching and Survivorship Administrator | - Maintain and execute matching and survivorship strategies on entities where Administrative permission is assigned - Maintain synonym lists - Accounts also having the System Administrator role may create needed control attributes as they create strategies. |
| Permission Administrator | - Modify permissions for entities where they have the Administration permission |
| Portal Administrator | - Create and maintain web applications hosted in FastApps Portal - Create and maintain forms and presentation views - Create and modify hierarchies using existing relationships |
| Quick Update Account | - Perform quick update actions |
| Rules Administrator | - Create and maintain data quality rules. - Requires Entity Administrator permission. |
| Super Administrator | - Can access all features and all data in the model - Can import and export accounts and teams (only accounts with this role can do so) Other permission and role assignments are irrelevant when this role is assigned |
| System Administrator | - Modify the model metadata - Change System Settings - Modify cluster servers - Can access all of the metadata in the model - Access model data only if granted permission through other assignments - Create new hierarchical relationships This role is system-wide and is not filtered by entity-level assignments |
| Account and Team Administrator | - Add accounts and teams - Edit accounts and teams (excluding permissions) - Delete accounts and teams Role is system-wide and is not filtered by entity-level assignments |
| Workflow Administrator | - Modify workflow registrations and forms - Configure VerifyMemberAddress activities You must also have the Address Verification Account or Address Verification Administrator role to configure VerifyMemberAddress. |

An account must be a member of a team to share reports with that team. This is true for non-administrative accounts as well as accounts with the Report Administrator role.