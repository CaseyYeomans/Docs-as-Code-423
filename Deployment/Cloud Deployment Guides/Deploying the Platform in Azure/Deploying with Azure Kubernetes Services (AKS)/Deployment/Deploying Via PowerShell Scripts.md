# Deploying Via PowerShell Scripts

The following is a step-by-step guide for deploying a Profisee container to Azure using PowerShell scripts. This process circumvents the ARM template deployment process entirely, and it is intended for environments with specific needs that require them to be deployed manually in this way. If your environment does not have any special considerations that prevent you from using the ARM template for deployment, [deploying the platform using the ARM template](https://support.profisee.com/wikis/profiseeplatform/deploying_the_AKS_cluster_with_the_arm_template) is the recommended deployment process.

## Prerequisites

### Licensing and Access

To run a container, you need a valid Profisee license that is associated to the DNS you will use for the environment and an access token for Profisee's container. This token is available via Azure Container Registry (ACR).

A Profisee license and ACR access token can be obtained by opening a support case to Profisee's support team. You will need to provide the DNS path for the environment that you will be creating. For example: *mdm.companyname.com*

Profisee's support team will provide the ACS access token and license file for inclusion in the Settings.json file (as outlined below).

### Deployment Utilities

Profisee uses PowerShell to execute the deployment Profisee into Azure. Administrators have two options for running PowerShell:

1. **Azure Cloud**: Use PowerShell hosted within the Azure Cloud Shell of the Azure Portal to execute the deployment.
2. **Local**: Use PowerShell locally, running on a Windows computer (a workstation or server).

PowerShell hosted in Azure includes all necessary pre-requisites. When running PowerShell locally, the following pre-requisites must be installed:

- [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
- The Azure CLI is used to execute commands against Azure.
- Version 2.5 or higher is required.
- [Chocolatey](https://chocolatey.org/install)
- Chocolatey is a software management solution. It is the commonly used for installing Helm (next pre-requisite).
- The link includes instructions for installing Chocolatey via PowerShell.
- [Helm](https://helm.sh/docs/intro/install/)
- Helm is used to manage Kubernetes applications. Profisee uses Helm to dynamically deploy Profisee containers into Kubernetes.
- The link includes instructions for installing Helm using Chocolatey in PowerShell.

### Azure Permissions

To deploy Profisee into Azure, you need an Azure AD account that has permissions to do the following:

- Create resource groups
- Create an Azure SQL Server and/or database (unless using existing)
- Create an Azure File Repository (unless using existing)
- Edit DNS Zones (unless you are using a DNS registry that is external from Azure)
- Edit/create Azure Active directory app registrations
- Create an Azure Kubernetes Service (AKS) cluster (unless using existing)

### Certificate

To secure communication, you must provide a certificate and its private key from a certificate authority. This certificate and private key will be specified as part of the environment configuration and used to secure network traffic using TLS.

The certificate can be a wildcard certificate such as \*.company.com, or it could be a specific certificate per Profisee environment that matches the DNS name of each environment. For example: *mdmdev.company.com* and *mdmprod.company.com*.

# **Setup**

## Step 1: Download GitHub Profisee Kubernetes Repository

Download the [GitHub Profisee Kubernetes](https://github.com/Profisee/kubernetes) repository to your local machine as a zip file, and un-zip it. This can be done from the **Clone or Download** button.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ia86e529330a7924f.png)

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i1e0b175c393bf722.png)

Alternatively, you can clone the GitHub repository using GitHub Desktop or GitHub bash. This is not necessary, as you should not be submitting pull requests to this GitHub repository.

## Step 2: Update Values.yaml file

In your downloaded GitHub repository is a Values.yaml file: *...\kubernetes-master\scripts\Values.yaml*

You must update this file with your Azure Container Registry access token (provided by Profisee's Support team), your Profisee License information (also provided by Profisee Support), and your certificate and associated private key.

1. Set the **image auth** value (provided by Profisee Support)
2. Set the **licenseFileData** value (provided by Profisee Support)
3. Set the **TLS certificate** value in Values.yaml
4. Set the **TLS key** value in Values.yaml

The following screenshot shows where this information should be updated in the Values.yaml file:

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-idfada8bbf95bb682.png)

The Values.yaml file is white space sensitive. Ensure you maintain consistent indentations and white space.

## Step 3: Set variables in DeployProfiseePlatform.ps1

The DeployProfiseePlatform.ps1 is the PowerShell script that will deploy an instance of Profisee into Azure. At the top of this script are multiple sets of variables that are inputs to the script. Each section is covered below.

### Resource Group

The Resource Group is a container used to house all services created as a part of this script.

```
###Resource group###

$createResourceGroup = $true #Set to false if you want to use an existing resource group (we recommend a new resource group ($true)).

$resourceGroupName = "resourcegroupname" #The resource group within which the new AKS cluster will be located.

$resourceGroupLocation = "eastus2" #Which Azure data center will this run in, ex: eastus2. Only necessary if creating a new resource group.
```

If you will be using existing Azure resources (ex. Azure SQL Database), it is recommended to create this resource group in the same location/data center as the other resources being used (ex. EastUS2)

### SQL Server

This specifies the SQL Server and database to be used by this Profisee environment.

```
###SQL###

$createSqlServer = $true #Set this to true if you want to create a new SQL Server. False if you want to use an existing Azure SQL Server.

$sqlServerResourceGroup = $resourceGroupName #(or specify the resource group of an existing Azure SQL Server)

$sqlServerName = $resourceGroupName + "sql" #(or specify the Name of an existing Azure SQL Server)

$sqlDatabaseName = "databasename" #(the database to create and/or use)

$sqlUserName = "username" #Self-explanatory

$sqlPassword = "password" #Self-explanatory
```

- You can use an existing SQL Server to host the Profisee database if preferred versus a dedicated SQL Server for Profisee.

- If the database name specified does not exist, Profisee will create a new "empty" database. If the database specified already exists, Profisee will attempt to upgrade that database to the latest Profisee schema. Ensure you backup the existing database prior to running the deployment.

- Profisee currently uses SQL Authentication for Azure SQL. A User Name and Password must be specified. Profisee persists this information as encrypted secrets on the AKS cluster and encrypts it securely on the container.

- If creating a new SQL Server, you should access that server via the Azure portal and size the server based on the guidelines in Profisee's Installation and Configuration guide.

- Your $sqlServerName must be globally unique. Once you create the server, Azure will reserve your server name for 5 days. If attempting to re-install after deleting the database, installation will fail if you attempt to recreate the database using the reserved server name.

### DNS

The DNS entry routes users to the external IP address of the ingress controller of the AKS cluster. By default, this script captures the external IP address of the ingress controller and registers a DNS entry for that IP address using the domain path specified.

```
###DNS###

$createDNSRecord = $true #Set this to true if you are using a DNS Zone in Azure. False if you're maintaining DNS somewhere else (we'll have to update that DNS entry manually).

$domainNameResourceGroup = "resourcegroupname" #This is the resource group of the DNS zone where the DNS record should be created/updated. You can find this in the Azure Portal.

$domainName = "yourdomain.com" #Typically the root domain of your company/organization. For example, Profisee's is Profisee.com

$hostName = "hostname" #Typically equivalent to the environment or machine name.
```

If you are managing DNS outside of Azure, you will need to capture the external IP address of the ingress controller and assign it to the DNS record in your external DNS registry.

### File Repository

The File Repository is used to store and manage unstructed data. This includes file attachments, workflow definitions, eventing subscribers, etc. You can use an existing storage account, or create a new one.

```
##File Repository###

$createFileRepository = $true #Set this to true if you want to create a new storage account. False if you want to use an existing storage account.

$storageAccountName = $resourceGroupName + "files" #(or specify an existing one if you're using an existing storage account)

$storageShareName.ToLower() = "files" #(or specify an existing one if you're using an existing storage account)
```

- You can use an existing storage account if preferred.

- You should always use the exiting storage account when upgrading between releases.

- Your $storageShareName must be all lowercase.

### Azure AD Application Registration

Registering the Profisee application with Azure Active Directory allows Azure AD to be aware of this application so that it can accept authentication requests and redirect the user back to Profisee once authenticated.

```
###Azure AD App Registration###

$createAppInAzureAD = $true #Set this to true if you haven't manually registered the application and redirect URI.

$azureClientName = "clientname" #Required if createAppInAzureAd = true. Unused if false.

$azureClientId = "" #Required if createAppInAzureAd = false. Unused if true.

$azureClientSecret = "" #Optional if createAppInAzureAd = true. Unused if false.
```

Instructions for creating this manually are included below "Special Scenarios" section.

### Profisee Administrator Account

The Profisee Administrator Account will be the user that is added as a Super User when initially configuring a new environment. This is typically the email address of the first user who will log-into the system and add other users.

Note that when using Helm to suspend and resume services, the process attempts to create this admin each time the container is deployed. This generates a non-fatal uniqueness validation error in SystemLog on startup.

```
###Profisee platform###

$adminAccountForPlatform = "emailaddress@domain.com" #This should be account of the first super user who will be registered with Profisee, who will be able to logon and add other users.
```

### AKS

This section is used to configure settings specific to AKS.

```
###AKS Settings###

$clusterVmSizeForLinux = "Standard_B2s" #The Linux node is used only for This should be fine, but we could change it if we determine we should. Used primarily for networking/load balancing controllers (Linux).

$clusterVmSizeForWindows = "Standard_B4ms" #We'll want to ensure the correct size

$kubernetesVersion = "1.17.3"

$windowsAdminUserName = "winadmin" #Username to create on Windows node VMs.

$windowsAdminPassword = "Ple@seCh@ngeMe1234!" #Password to create on Windows node VMs.
```

- The Linux nodes are used to host some Kubernetes services, as well as the NGINX networking controller. These can typically be lightweight VMs.

- The Windows nodes are used to host the Profisee Application. These should be sized in accordance with guidance in the Profisee Installation and Configuration guide.

- The Kubernetes Version should generally be the latest GA version available in AKS.

- The Windows Admin Password cannot contain numbers.

## Step 5: Execute PowerShell script

1. Run the powershell script: DeployProfiseePlatform.ps1
2. Wait approximately 20 minutes for the deployment process to finish.

The script will be faster if fewer resources are being created. For example, it will take longer when creating a new SQL Server/database and file repository versus using existing resources.

The shell will output the "helm install" command for creating the NGINX networking controller and Profisee environment. It is recommended you capture these commands so you can quickly turn this environment on and off.

## Step 6: Verify Deployment and Troubleshooting

1. The initial deploy will have to download the container which takes about 10 minutes. Verify it has finished downloading the container:
1. kubectl describe pod profisee-0
2. Monitor the status of the pod and wait for "Pulling" to finish
2. You can interactively access the container via PowerShell using the following command:
1. kubectl exec -it profisee-0 powershell
3. Once you are accessing the container via PowerShell
1. You can see if the Profisee Windows Service is running using the following command:
1. Get-Service Profisee
2. System logs can be accessed with the following command:
1. Get-Content C:\\Profisee\\Configuration\\LogFiles\\SystemLog.log

## Special Scenarios

### Manually creating application registration

In some scenarios it may be preferred to create the application registration manually in advance instead of automatically via the PowerShell script. This is often necessary when the ownership and management of different Azure resources is distributed across an IT organization.

Each Profisee environment (for example, development, test, and production environments) should have their own application registration. To manually create an application registration in the Azure Portal.

1. Login to the Azure Portal
2. Open your organizations Azure Active Directory resource (use the search bar if it does not appear on your home page)
3. In Resource Menu on the left hand side of the page, select "App registrations"
4. In the Command Bar at the top of the page, click "New registration"
5. Specify the following:
1. Name - Something descriptive like "Profisee Production"
2. Supported account types - Typically "Accounts in this organizational directory only"
3. Redirect URI
1. The type should be "Web"
2. The URL is the root DNS of your site, plus "/profisee/auth/signin-microsoft". For example, if your DNS path is <https://profisee.company.com>, the Redirect URI should be <https://profisee.company.com/profisee/auth/signin-microsoft>.
Note that the Redirect URI is case-sensitive.
6. Click "Register"
7. Navigate to the new registration -> Authentication
8. Under "Implicit grant" check the box for "ID tokens"
9. Click Save
10. Navigate back to the overview page for the new app registration.

When creating the application registration manually, set the $createAppInAzureAD variable to "false": $createAppInAzureAD = $false

### Manually configuring DNS entry

Organizations that are not using Azure DNS zones to host DNS records will need to register the external IP address of the Kubernetes Ingress Controller with their DNS registry. To do this, you will need to find the IP address created during the deployment so you can associate your DNS entry with it.

1. Open PowerShell
2. Run the following command:
1. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibb395b6e2eed2e7d.png)kubectl describe pod profisee-0 kubectl describe services nginx-nginx-ingress-controller![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-id8322681edd144c5.png)
3. Note the External IP address of the ???, which should be associated to a DNS record in your chosen DNS registry.

### Using an existing AKS Cluster

Organizations that have existing AKS Clusters can run Profisee inside that cluster alongside other container workloads. However, you are responsible for providing an AKS environment/configuration that is compatible with Profisee. While Profisee's support team can provide general guidance, we cannot make recommendations or guide you in making changes to the configuration of your existing environment as we do not want to risk breaking other workloads. The following outlines some high-level requirement for Profisee to run alongside other workloads in a shared AKS cluster:

1. Profisee runs on Windows Containers. An AKS Cluster must have a Windows Node Pool to host the Profisee container.
2. Profisee uses NGINX for networking and ingress control. Profisee requires several changes default NGINX settings. These can be viewed in the nginxSettings.yaml file.

When using an existing AKS Cluster, you will likely need to run the Helm commands manually to deploy Profisee to that AKS Cluster.

### Uninstalling and Reinstalling Profisee

You can quickly turn the Profisee container "off" and "on" using Helm. You can do this using the helm command that is output to the screen when the PowerShell script is executed.

To uninstall a Profisee container (i.e. turn it off), run the following command:

```
helm uninstall profiseeplatform2020r1 profisee/profisee-platform
```

To install the Profisee Platform, run the original helm command:

```
helm install profiseeplatform2020r1 profisee/... [Your settings here]
```

You can externalize all of the command line switches by adding them to the Settings.json file. Simply remove each setting from the helm command and specify it in the Settings.json file. This allows for the Settings.json file to drive the deployment dynamically and is something that can easily be checked into and managed via source control.

###