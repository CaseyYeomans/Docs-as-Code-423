# Configuration Manager (New Installation)

---

### Installing the Profisee Platform

Observe the following steps to install the Profisee Platform in an on-premise environment.

1. Log in to Server with an AD Account with Windows Admin access (does not have to be the Service Account).
2. Get the Username/Password for the SQL SA Account and the AD Service Account.
3. Get the .plic license file that matches the server name from Profisee Support.
4. Download the install files from the Downloads folder on Profisee Community.
5. Install the Profisee Platform MSI to the default location in C:/Program Files/Profisee or a custom location.

### Run the Profisee Configuration Manager

6. For a new setup, select "Create a New Cluster".

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i1907a692cd4dd6cf.png)

7. Apply the *.plic* license file for this server.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iba9a7e11885714b0.png)

### Configure Authentication

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ib0f66490e9c2763b.png)

8. Choose the first Administrator Account.

> [!NOTE]
> The Administrator Account should be a service account you can log in with. It will be used to run system processes such as Data Quality rules. This account should not be a member of the Local Administrators group.

9. Check the **Active Directory** checkbox and add a label for the Windows Authentication option
10. Configure OIDC Auth Providers. For Claims Mappings for Entra, OKTA, or Google, see [here](https://support.profisee.com/wikis/profiseeplatform/oidc_provider_info_and_claims_mappings).
11. Click **Next** to Continue.

### Configure the Web Application

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic82e627eaa3ae0f9.png)

12. Configure the DNS URL (Optional). This option adds preferred DNS URL for reaching the server that matches the SSL-certified FQDN - <https://myservername.domain.com>. The DNS URL must match the name on your SSL Certificate and the DNS URL in your license file
13. Select the website that the web application should be added under (**Default Web Site**is recommended).
14. Check the HTTPS option, which is automatically selected if your DNS URL is entered with HTTPS.

> [!NOTE]
> This option is not available before you configure the HTTPS binding in IIS. If you do not have HTTPS configured with a valid Certificate, you will receive the following warning.

15. Create Profisee Web Application ("Profisee" recommended).
16. Create App Pool  ("Profisee" recommended) and enter your AD Service Account Username and Password.

> [!CAUTION]
> Do NOT use the DefaultAppPool or .Net 4.5 App Pools.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-if0a0f9bb819ab4ad.png)

17. Click **Next** to Continue. A warning will pop up if you do not have the preferred URL set up in the **Host Header** of the HTTPS binding, which is security best practice.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5bec2df9d9331ccb.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-icf748968e8d22b7f.png)

### Configure SQL Server Connection

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i52758931ed8e9001.png)

18. If you are not using a local SQL Server delete the dot (.) from the Server Name and enter the SQL Server name or PaaS SQL URL.
19. Choose your Authentication method. Windows Authentication and SQL Authentication are available for OnPrem/IaaS, and SQL Authentication is only available for PaaS SQL. Entra Authentication and others are not available for PaaS.
20. Enter the Username and Password for the Authentication type selected.

> [!NOTE]
> The user must have the SysAdmin role in OnPrem/IaaS or be the SQL Admin User in PaaS. See System Requirements for Profisee Server for more information. The admin user will be used only during Configuration, then the SQL access will run under the User created for the service account, or a generated SQL Auth user. This account should not be a member of the Local Administrators group.

21. Test the connection and click **Next** to continue.

### Configure Database

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i7e55f00682a85397.png)

22. Enter a name for new Profisee Database ("Profisee" recommended).
23. Select a Collation for the Database ("Default" recommended). Profisee does not support Case Sensitive (SC) collations.
24. Check box for **Create New Database.**This option should be checked automatically.
25. Click **Next** to Continue.

### Configure Windows Service

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i6152c42ed80a1042.png)

26. Enter the Port Number for Windows Service installation (8003 recommended). Choose a different port if 8003 is in use.
27. Enter your AD Service Account Username and Password, and confirm the Password.
28. Choose the type of user that will be created in the Database to get the service account permissions.

> [!NOTE]
> The user can be a Windows Auth user and use the account configured above, or a generated SQL Auth user. If you want to be able to move the DB to Azure at a later time, then choose SQL Auth User.

### Configure File Repository

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iffeda18832e93c37.png)

29. Enter a File Repository Folder Path such as *C:\ProfiseeFiles* or *\\ProfiseeFiles* for a network share. If you are using a Cloud only configuration with OIDC Auth only you must configure a Cloud Storage Account and File Share path.
30. Enter the AD Service Account Username and Password, and confirm Password. The account must have read/write permissions to the File Repository folder.
31. Select a Login Type. The login type must be AD Credentials for an On-Premise installation. For OIDC Auth choose Non-AD Credentials. If you are encountering issues with the service using AD Credentials, try again using non-AD credentials.
32. Test Connection to verify read/write permissions. If using an account different than the one for the App Pools, make sure the App Pool Service account also has Read/Write permissions for the Fire Repository folder.
33. Click **Next** to Continue.

### Configure Governance (Optional)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i390c61820c62b9b0.png)

34. Select a Governance Provider. Choose **None** if you do not want to configure Governance at this point. Choose Azure Purview if you already have a working instance of Azure Purview you would like to integrate with Profisee. If you want to configure Purview, follow these steps, see the [Purview Integration Guide](https://support.profisee.com/wikis/profiseeplatform/azure_preview_overview). Select Alation to integrate the Profisee Platform with Alation.  Review the official [Alation documentation on managing connections](https://docs.alation.com/en/latest/OpenConnectorFramework/InstallandManageConnectors/ManageConnectors/index.html) for more information on integrating with Alation.
    34. Fill out the Azure Purview Connection Options which you collected from your working instance of Azure Purview.
        * **Azure Tennant ID**: Your Azure Tenant ID is located in the Azure AD web portal under Azure Active Directory > App Registrations.
        * **Purview API URL**: This is the Purview (Apache) Atlas endpoint that appears in the Properties blade of your Purview account in the Azure Portal.
        * **Purview Service Principal ID**: This is the Client ID of your App Registration created as part of the prerequisite setup.
        * **Purview Service Principal Secret**: This is the Client Secret you generated and recorded during the prerequisite setup.
    35. Fill out the Alation connection options collected from your Alation environment.
        1. **Base URL**: The URL for your Alation environment. This can be located in Alation under Connection Settings > Alation Base URL.
        2. **Username**: The username for your Alation login. This account must have Super Administrator permissions.
        3. **Password**: The password for your Alation login.
35. If desired, select a pre-configured Collection, or click the **+** button to create a new Collection.
36. Click **Next** to Continue.

### Review Summary

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i60633fddae1ec654.png)

38. Save the listed information for future reference when configuring options.
39. Click **Next** to Continue.

### Review Configuration and look for Succeeded status on all steps

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i4f3a3d45ba9c00a0.png)

40. Check the REST Health page to ensure all services are configured and running properly.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibf00211b897faaca.png)

---