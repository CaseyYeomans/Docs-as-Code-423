# Prerequisites for Integrating with Purview

Profisee Purview requires the deployment team to satisfy the following prerequisites before deploying the Profisee Platform with the Purview governance features:

1. You must establish an Azure App Registration that acts as the service account that is used by Profisee's data governance integration subsystem to communicate with Purview.

2. You must have an existing, or create a new, Azure Purview Account as a resource within your Azure subscription in advance of configuring and deploying Profisee's Purview.
3. You must assign the App Registration with the Data Curator and Collections Admin roles for your Purview account.

Details of these steps are covered in the subsections below.

## Creating an Azure App Registration for use by Profisee

Profisee uses an App Registration to access information in both Purview but also user and group data in Azure Active Directory (AAD). It needs access to Purview to obtain governance data while it accesses to AAD to reconcile user and group ID information obtained from Purview to user and group details such as name, phone number, email address, and profile picture. To create your App Registration, perform the following:

1. Navigate to Azure Active Directory in the Azure Portal.

2. Select App Registration from the Manage menu of your associated AAD resource.

3. Select New registration from the App registrations menu.

4. Give your new App Registration a unique Name within the context of the AAD resource and click Register. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i62a90509969d332a.png)

Once you have created your new App Registration, you need to grant it the following API Permissions in AAD to allow Profisee to access user and group information in AAD:

- Group.Read.All
- GroupMember.Read.All
- User.Read
- User.Read.All

To grant these privileges:

1. Click on your newly created App Registration to open it and select **API permissions** in the **Manage** menu. By default, the App Registration will already have User.Read permission.

2. Click**Add a permission** in the **API permissions** menu.

3. Click on Microsoft Graph in the Commonly used Microsoft APIs list.

4. Click on **Application permissions** in the permission type selection related to the**What type of permissions does your application require?** question.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i9da933db7c9baf74.png)
5. Type 'user' in the **Select permissions** search box.
6. Expand the **User** permissions list and select the **User.Read.All** permission checkbox.
7. Type 'group' in the **Select permissions** search box.
8. Expand the **Group** permissions list and select the**Group.Read.All**permission checkbox.
9. Expand the **GroupMember** permissions list and select the **GroupMember.Read.All** permission.
10. Click **Add permissions** button to save the permissions.

Your configured permissions should now appear as shown in the figure below: ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i8dfdadd66613db45.png)

If you do not have administrative rights to your Azure Active Directory resource, the Grant admin consent button will be disabled, and you will not be able to directly assign the specified roles and you will see the warnings as shown in the figure below. You will need to request that your AAD administrator consent to your request for the assigned roles.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i61ce9de0817a68c1.png)

The last step is setting up your App Registration is to generate a client secret that represents the password that is used by Profisee to authenticate itself before being granted access to Purview and AAD. To generate a new client secret, perform the following steps:

1. Open your App Registration from AAD.
2. Click on **Certificates & secrets** from the **Manage** menu.
3. Under the **Client secrets** section, click on**New client secret**.
4. Give your secret a**Description** and select an **Expires** duration, then click**Add**.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-if6a03bde76ccd36e.png)
5. After the client secret has been created, you must immediately copy the secret Value because you are only able to see and copy this value once. After the page refreshes, the secret will be gone, and you must create a new secret to access another value. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i73a38ee13c8dc54e.png)

Save the secret in a safe location like a password vault or secured text file as you will need it later during the Profisee deployment.
6. Return to the Overview tab of your App Registration and copy the Application (client) ID value and store it in a safe and convenient location as you will need it while deploying Profisee.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5108488524cb8d26.png)

Now that you have an App Registration fully configured, you can move on to setting up your Purview account.

## Creating an Azure Purview Account

During the Profisee deployment you must specify the App Registration along with the Purview account details so Profisee can communicate with Purview. Having access to a Purview account is a prerequisite to configuring Profisee's integration with Purview.

If you have not yet created a Purview account, you must create one before configuring integration with the Profisee Platform. To create a Purview account, perform the steps outlined in [Create an Azure Purview account instance](https://docs.microsoft.com/en-us/azure/purview/create-catalog-portal#create-an-azure-purview-account-instance).

After creating your account (or if you already have a Purview account set up), you will need the **Atlas Endpoint** during the Profisee deployment/configuration process. This endpoint is the base rest endpoint URL that Profisee uses to communicate with Purview.

In addition to the Atlas Endpoint,, you will also need the App Registration client ID and secret created in **Creating an Azure App Registration for use by Profisee** above.

To access this information, go to your Purview account in the Azure Portal and view the Properties blade as shown below: ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i46985e467d6aa51d.png)

Once your account has been created, your deployment steps will vary depending on if you are attempting to deploy an IaaS or PaaS/SaaS Solution, and then again if the solution is a private deployment or a public deployment.

- For an **IaaS solution**, you must have the **Purview Data Curator** and **Collections Admin** permissions at the **root collection** level in Purview.
- For a **PaaS/SaaS solution**, you must have the **Purview Data Curator** and **Collections Admin** permissions at the **collection** level in Purview.

Perform the following steps to assign the **Purview Data Curator** and **Collections Admin**roles to your App Registration:

1. Navigate to your Azure Purview account in the Azure Portal.

2. Open Purview Studio

3. Click the Data Map icon.

4. Select **Collections**, then **Role Assignments**.
5. Click the icon to the right of the role assignment name (**Purview Data Curator,** **Collections Admin,** or **Data Product Owners**).

The **Data Product Owners**rile is in the Data Catalog within the Roles section of a Governance domain. Unlike Collections, domains can exist by themselves, but they can also have a parent domain. If they have a parent domain, the roles can be inherited from that parent, or they can be set separately on that child domain. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5f8ad9522ff1f19e.png)

6. Type the name of the App Registration you created in the *Creating an Azure App Registration for use by Profisee*section above.

7. Click the App Registration shown in the list of users, groups, and service principals. This adds your App Registration to the list of selected users, groups, and/or service principals as shown below:
8. Click **OK** to assign the role to your App Registration, then repeat for the other roles.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-idee7f5f2cdedbd96.png)

#### Public and Private Deployments

If you are configuring a **public deployment**, you will need the following pieces of information:

- **Tenant ID**: This ID is required for Azure Entra, where Purview is hosted. This can be found by pulling your Tenant ID [here](https://portal.azure.com/#view/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/~/Overview).
- **Purview Account Name**: This can be found by locating your Purview account properties and pulling the Atlas endpoint.
- **App Registration:** Located in Azure Entra.You must create an app registration as per the page and enable the *User.Read.All*, *Group.Read.All*, and *GroupMember.Read.All* permissions. If these permissions are not enabled, Profisee has limited usability with Purview and will not be able to display crucial portions of metadata.
- **App Registration Secret**: This is required for the App Registration above.
- **Purview Collection ID**: If root, this will be the same as the Purview account name. If not, this will be a 6-digit alphanumeric ID. You can locate your Purview Collection ID by visiting your Microsoft Purview Governance Portal. Go to the collection where you would like Profisee to deploy. Your URL will look like the following: *web.purview.azure.com/resource/YourPurviewAccountName/main/datasource/collections?collection=**ThisIsTheCollectionId**&feature.tenant=**YourAzureTenantId***

If you are configuring a **private deployment**, you will need the above pieces of information as well as the following:

- **For IaaS/PaaS**
- Create a *Purview Private DNS Zone.*
- Create a private endpoint for Purview in that zone.
- Link the Private DNS Zone to the Vnet where Profisee is hosted (for either AKS or a VM).
- **For SaaS**
- Locate your Purview Resource ID.
- Approve all requests to create two private endpoints to be used by the Profisee instance running in SaaS.

### Profisee MDM Glossary Term

Finally, you should ensure Profisee MDM is added as a Glossary Term before finishing configuration.

1. Navigate to **Data Catalog** > **Catalog Management** > **Governance Domains.**
2. Select **Glossary Terms** from the Business Concepts header.
3. Click **Create Term** and add *Profisee MDM* as the glossary term name and a description like, "Assets are associated with and related to Profisee MDM."

### Finish

Once this is complete, you now have a Purview account and your App Registration has been granted rights to curate (i.e. add, update, and delete) data in your Purview data catalog. You are now ready to deploy the Profisee Platform Purview integration. You have two options for deployment. If you are planning to deploy the Profisee Platform in Azure using the ARM template, refer to the instructions in [Purview Integration in a Profisee Azure AKS Deployment](https://support.profisee.com/wikis/profiseeplatform/deploying_the_purview_preview_in_an_azure_paas_environment). If you are planning to deploy on-prem, complete the information in the Governance section of the [Configuration Manager](https://support.profisee.com/wikis/profiseeplatform/configuration_manager_new_installation) during installation.

###