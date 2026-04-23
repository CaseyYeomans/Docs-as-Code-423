# Planning Your Managed Identity Configuration

A Managed Identity allows an Azure service (in this case, the various steps within the Profisee AKS ARM template deployment process) to authenticate itself with various Azure services that support Azure AD authentication. Without associating a Managed Identity with the Profisee's AKS ARM template deployment process, the steps within the process would be unable to create and configure the resources that are provisioned during deployment.

Before you start the deployment process, you must create and/or have properly configured a **User-assigned Managed Identity** that provides credentials for the deployment process to provision and configure resources during the deployment process. For additional details on what a Managed Identity is and its purpose, refer to [What are managed identities for Azure resources?](https://docs.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview) on the Microsoft documentation website.

The configuration requirements of the Managed Identity are driven by the following questions:

- Do you want to create a dedicated Resource Group to contain all the resources associated with the Profisee AKS cluster, or do you want to co-mingle these resources in an existing resource group?

Profisee generally recommends using a dedicated Resource Group to easily manage these resources within Azure. For example, by using a dedicated Resource Group, the cluster resources can easily be decommissioned by simply removing the associated Resource Group.

- If you want to create a dedicated resource group, do you want to create this group manually in advance of the deployment, or do you want the deployment process to create this group automatically as part of the deployment process?
- If you are using an existing group or creating the group manually, do you want to allow the deployment process to automatically update your DNS with the host names provisioned in the cluster or will you or your network administrator(s) choose to update your DNS manually?
- Do you want the deployment to automatically create the Azure App Registration in Azure AD during the deployment process?

The following decision tree outlines the decision points and actions that should be taken based on the answers to the questions above. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ib1e984b25a7a9f9.png)

The following action must be taken depending on the decisions outlined above:

**If you choose to use an existing Resource Group, you must:**

- Identify the Resource Group name as you will need to specify this in the **Resource Group** property of the ARM template.
- Ensure there is a Managed Identity created that has Contributor rights to this Resource Group. If there is not a Managed Identity, you must create a new Managed Identity through the Azure Portal or CLI and grant it Contributor rights to the target Resource Group. Record the Managed Identity and its associated Resource Group as you will need these when specifying the **Managed Identity Name** and **Managed Identity Resource Group** properties of the ARM template.

**If you wish to manually create a new Resource Group in advance of the deployment process, you must:**

- Create a new Resource Group through the Azure Portal or CLI. Record the name of the Managed Identity as you will need to specify this in the **Resource Group** property of the ARM template.
- Create a Managed Identity that has Contributor rights to the Resource Group created above. Record the Managed Identity and its associated Resource Group as you will need these when specifying the **Managed Identity Name** and **Managed Identity Resource Group** properties of the ARM template.

**If you want to allow the Profisee AKS ARM deployment process to create a new Resource Group during the provisioning process, you must:**

- Create or have access to a Managed Identity that has Contributor rights to the Subscription to allow the Profisee AKS ARM deployment process to create the Resource Group in the Subscription during deployment. If there exists a Managed Identity you wish to use, ensure it has Contributor rights to the Subscription. If not, you can create a new Managed Identity and grant it Contributor rights to the Subscription. Record the name and Resource Group associated with this Managed Identity as you will need to specify these in the **Managed Identity Name** and **Managed Identity Resource Group** properties of the ARM template.

**If you want to allow the deployment process to automatically update your DNS with host names provisioned in the cluster:**

- You must ensure that the Managed Identity created and/or configured in the actions listed above has Contributor access to the Resource Group that contains your DNS resource.
- If the DNS is in the same resource group to which you plan to add the Profisee cluster resources, there is nothing else to do. However, if the DNS is in a different resource group, you must also grant Contributor rights to the Managed Identity to the DNS's resource group.
- Make sure to record the DNS's host name, domain, and Resource Group as you will need these when specifying the **DNS Host Name**, **DNS Domain Name**, and **DNS Domain Resource Group** properties of the ARM template.

If you choose to manually update your DNS server, the Profisee cluster will deploy but will be unreachable and, thus unusable, until your DNS is updated with the host name and address provisioned in the cluster. Once the cluster has been deployed, you can find the information needed to update the DNS from the Azure Portal by following the navigation path below:

**Resource Groups > [Profisee Cluster Resource Group Name] > Access Control (IAM) > InstallProfiseePlatform > Outputs**

**If you want the deployment process to automatically add the Application (App) Registration for the Profisee AKS cluster to Azure AD as part of the deployment process, the Managed Identity must be assigned the Application Developer role inside Azure AD. Use the Azure Portal to assign this role:**

1. Navigate to your Azure AD resource inside your Subscription.
2. Click on **Roles and administrators** on the Manage menu.
3. Select the **Application Developer** role from the list of roles displayed.
4. Select **Add Assignment** on the role menu.
5. Search for the Managed Identity you plan to associate with the deployment process and the click the **Add** button to assign it the role.

If you choose not to automatically add the App Registration, you must create it manually and the record the Client Id associate with it as you will need this for the **Active Directory Client Id** property.

Profisee recommends automatically creating the App Registration as it is simpler and more efficient.

Once you have completed the actions associated with the decision points above, your Managed Identity, Resource Group(s), and Azure AD should be ready for the deployment process. Remember to record the following ARM properties and have the information at hand when you start the deployment process:

- Resource Group
- Managed Identity Name
- Managed Identity Resource Group
- Active Directory Create App (Yes / No)
- Active Directory Client Id
- DNS Update (Yes / No)
- DNS Host Name
- DNS Domain Name
- DNS Domain Resource Group

You are now ready to continue to [Planning Your SQL Server Configuration](https://support.profisee.com/wikis/profiseeplatform/planning_your_sql_server_configuration), or return to the [Planning Your Deployment](https://support.profisee.com/wikis/profiseeplatform/deploying_profisee_using_the_arm_template).

### See more

- [Planning Your Deployment](https://support.profisee.com/wikis/profiseeplatform/deploying_profisee_using_the_arm_template)
- [Planning your SQL Server Deployment](https://support.profisee.com/wikis/profiseeplatform/planning_your_sql_server_configuration)
- [Glossary of Azure and AKS Terms](https://support.profisee.com/wikis/profiseeplatform/glossary_of_azure_and_aks_terms)