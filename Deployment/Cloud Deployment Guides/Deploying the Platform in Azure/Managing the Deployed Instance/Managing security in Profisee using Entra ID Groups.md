# Managing security in Profisee using Entra ID Groups

By treating a group as a user in Profisee, you can use Entra ID groups for security permissions. To do so:

1. To determine if the Groups Claim token is set up correctly, please run the following command, replacing the variable with the client ID of the application registration used by Profisee.

```
az ad app list --app-id $AppRegClientId --query "[].groupMembershipClaims" -o tsv
```

2. Create Groups in Entra ID.

It is recommended to give them names such as *ProfiseeDev\_Admins*, *ProfiseeQA\_Admins*, *ProfiseeProd\_Admins*, *ProfiseeDev\_CRUD*, *ProfiseeDev\_ReadOnly* or *ProfiseeDev\_Stewards* or a similar naming convention for what that group would do in the particular Profisee instance. This makes it easier for Azure Admins to manage the group members easily. Have your Azure admin share those Group Names and Object IDs with the Profisee admin.

3. Add the users to those Entra ID groups.
4. If the command in step 1 above returns something other than **ApplicationGroup**, fix it by deleting the existing groups claims configuration in the App Registration and add a groups claim configuration. You must select the correct groups claim type. Groups claims work only with the 4th option shown below.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-idaa876933bb184b1.png)
5. Navigate to the **User/Groups**tab in the enterprise application, remove any existing users, and add the groups. Do not add new users.
6. Navigate to **Properties** in the enterprise application and switch the **Assignment Required** toggle to **Yes**.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i85de883c680f496.png)
7. Navigate to **Permissions** under **Security** and grant Admin consent so individual users are not prompted.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i6295a49980bdc066.png)
8. Navigate to the **Accounts and Teams** tab in Profisee and add the above group's object ID to a Group Account.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i107dedf6a99fc9b.png)
9. Edit the group name in the description to match the name in Entra ID. The description makes it easier for the Profisee admins to ensure permissions are as intended.
10. Grant the group the correct Roles, Teams and Permissions.