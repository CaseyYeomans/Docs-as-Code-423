# Deploying and Connecting to the Cluster

## Set-Up Managed Identity

Set up a Managed Identity to be used when deploying AKS and grant it the needed permissions. Permissions are granted at a subscription level.

#### **Create Managed Identity**

az identity create -g -n Get

#### **Object ID of Managed Identity**

az identity list

#### **Assign DNS Zone Contributor Role to MI**

The managed identity can have DNS Zone Contributor Role either on the parent resource group of the private DNS Zones (a possible option if all of the private DNS Zones are in the same resource group), or the DNS Zones themselves. The second option is more secure, but will require using this command to target each DNS Zone.

az role assignment create --role "DNS Zone Contributor" --assignee --scope <DNSZoneResourceID>

## Deploy AKS Cluster

When creating the AKS Cluster, we will deploy it as a private cluster using UDR as the egress path. Our initial command will create the Linux node pool, but we will have to add the Windows node pool that runs Profisee in a follow up command.

This is also the point where the node resource group and its resources will be automatically generated. The node resource group will contain the *kubernetes-internal ingress*, the Virtual Machine Scale Sets for the Windows and Linux node pools, a Network Security Group, and the *kube-apiserver* private endpoint and its NIC. These resources will be tied to the lifecycle of the AKS cluster. Note that because the *kube-apiserver* private endpoint is automatically created, you will not have to create a manual private endpoint for AKS.

Choosing too small of a network may result in problems during node/pod upgrades and regular operations. Each node and pod consume an IP, and while each Profisee pod consumes a single IP, you may choose to have additional security and monitoring pods that run alongside the regular cluster pods. Choose the node VM size and the OS disk size to be values appropriate for your environment.

### Deploy AKS Cluster with Linux Node Pool

Azure documentation for: [az aks](https://docs.microsoft.com/en-us/cli/azure/aks?view=azure-cli-latest)

*All the values should be in accordance with your networking infrastructure and security requirements, and are provided as an example. If you omit the kubernetes-version Azure will deploy the current default AKS version.*

*In this command we have enabled monitoring--this will create a default log analytics workspace used for monitoring analytics. This is a recommended but optional parameter; if your organization strictly controls the deployment of resources, you may run into issues when deploying using this command.*

*If you are deploying AKS behind a proxy, you must specify proxy configuration at deployment time, using the flag --http-proxy-config and a JSON file.*

```
az aks create -n <AKSCluster> -g <AppResourceGroup> --nodepool-name <LinuxNodePool> --node-count 1 --node-osdisk-size 100 --node-vm-size Standard_D2_v5 --enable-addons monitoring --enable-private-cluster --kubernetes-version <VersionNumber> --no-ssh-key --vm-set-type VirtualMachineScaleSets --network-plugin azure --outbound-type userDefinedRouting --vnet-subnet-id <AKSSubnetResourceID> --service-cidr 10.100.0.0/24 --dns-service-ip 10.100.0.10 --docker-bridge-address 172.17.0.1/16 --enable-managed-identity --assign-identity <ManagedIdentityResourceID> --private-dns-zone <AKSDNSZoneResourceID> --disable-public-fqdn --dns-name-prefix <DNSNamePrefix> --enable-oidc-issuer --enable-workload-identity
```

## Deploy Jumpbox

*You will need a method of connecting to the jumpbox once deployed. The easiest method is to deploy with a Public IP, but we are deploying with Azure Bastion to demonstrate what the process might be like if you have additional security requirements.*

Create Public IP for Bastion

```
az network public-ip create --resource-group <AppResourceGroup> --name <BastionIp> --sku Standard --location <Location>
```

Create Bastion

```
az network bastion create --name <BastionName> --public-ip-address <BastionIP> --resource-group <AppResourceGroup> --vnet-name <HubVirtualNetwork> --location <Location>
```

### Deploy Jumpbox

Azure documentation for: [az vm](https://docs.microsoft.com/en-us/cli/azure/vm?view=azure-cli-latest)

```
az vm create --name <VirtualMachine> --resource-group <AppResourceGroup> --image <Image> -- vnet-name <SpokeVirtualNetwork> --subnet <AppSubnet> --admin-username <USERNAME> --admin-password <PASSWORD>
```

From this point forward, all of the commands should be run from the jumpbox VM.

### Install Azure CLI on Jumpbox

```
Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi; Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'; rm .\AzureCLI.msi
```

### Install Chocolatey Package Manager on Jumpbox

```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

### Install helm on Jumpbox

```
choco install kubernetes-helm
```

### Install kubectl on Jumpbox

```
choco install kubernetes-cli
```

### Sign in with Azure CLI

```
az login
```

### Set Subscription

```
az account set --subscription <AzureSubscription>
```

### Add Windows Node Pool

Azure documentation for: [az aks nodepool](https://docs.microsoft.com/en-us/cli/azure/aks/nodepool?view=azure-cli-latest)

*Note: Windows nodepools' names must be 6 characters or less*

```
az aks nodepool add --resource-group <AppResourceGroup> --cluster-name <AKSCluster> --name <WindowsNodePool> --os-sku Windows2019 --os-type Windows --node-count 1 --node-vm-size Standard_D4_v5
```

## Connect to Cluster

### Connect to the Cluster

Azure documentation for: [az aks](https://docs.microsoft.com/en-us/cli/azure/aks?view=azure-cli-latest)

```
az aks get-credentials --resource-group <AppResourceGroup> --name <AKSCluster>
```

### Create Profisee Namespace

Create namespace and authenticate with the code provided.

```
kubectl create namespace profisee
```

### Key Vault Specific Set-Up (Optional)

If key vault is to be used, the following additional steps are needed. Make sure that you have authenticated to the cluster with the az aks credentials command above.

### Install the secrets store CSI Driver and Azure Key Vault Provider

```
helm repo add csi-secrets-store-provider-azure https://azure.github.io/secrets-store-csi-driver-provider-azure/charts
helm repo update
helm install -n profisee csi-secrets-store-provider-azure csi-secrets-store-provider-azure/csi-secrets-store-provider-azure --set secrets-store-csi-driver.syncSecret.enabled=true
```

### Install Workload Identity driver

If running a build from September 2023 or older, you may need to migrate your AAD Pod Identity driver to the Workload Identity driver. For more information, click [here](https://support.profisee.com/wikis/profiseeplatform/Migrating_from_AAD_Pod_Identity_to_Workload_Identity).

```
$RESOURCEGROUPNAME=<ResourceGroupName>
$CLUSTERNAME=<AKSClusterName>
az aks get-credentials --resource-group $RESOURCEGROUPNAME --name $CLUSTERNAME --overwrite-existing;
$OIDC_ISSUER="$(az aks show -n $CLUSTERNAME -g $RESOURCEGROUPNAME --query "oidcIssuerProfile.issuerUrl" -o tsv)"
$identityName="AKSKeyVaultUser"
$AKSINFRARESOURCEGROUPNAME ="$(az aks show -n $CLUSTERNAME -g $RESOURCEGROUPNAME --query "nodeResourceGroup" -o tsv)
az identity federated-credential create --name ProfiseefederatedId --identity-name $identityName --resource-group $AKSINFRARESOURCEGROUPNAME --issuer $OIDC_ISSUER --subject system:serviceaccount:profisee:profiseeserviceaccount --audience api://AzureADTokenExchange
```

### Assign roles

Azure documentation for: [az role assignment](https://docs.microsoft.com/en-us/cli/azure/role/assignment?view=azure-cli-latest)

*Assign roles to the AKS agent pool managed identity (<ClusterName>-agentpool, ex. ProfiseeAKSCluster-agentpool) which is automatically created by the AKS deployment.*

### Managed Identity Operator to the App Resource Group

```
az role assignment create --role "Managed Identity Operator" --assignee <AKSCluster-agentpoolManagedIdentityObjectID> --scope <AppResourceGroupResourceID>
```

### Managed Identity Operator to the Node Resource Group

```
az role assignment create --role "Managed Identity Operator" --assignee <AKSCluster-agentpoolManagedIdentityObjectID> --scope <NodeResourceGroupResourceID>
```

### Virtual Machine Contributor to the Node Resource Group

```
az role assignment create --role "Virtual Machine Contributor" --assignee <AKSCluster-agentpoolManagedIdentityObjectID> --scope <NodeResourceGroupResourceID>
```

## Create Key Vault Identity and Assign Roles/Permissions to it

Azure documentation for: [az identity](https://docs.microsoft.com/en-us/cli/azure/identity?view=azure-cli-latest)

*Create a Managed Identity in the Node Resource Group that will be used to access the Key Vault*

```
az identity create -g <NodeResourceGroup> -n <KeyVaultManagedIdentity>
```

### Assign Required Permissions to Key Vault Identity

Azure documentation for: [az role assignment](https://docs.microsoft.com/en-us/cli/azure/role/assignment?view=azure-cli-latest), [az keyvault](https://docs.microsoft.com/en-us/cli/azure/keyvault?view=azure-cli-latest)

**If key vault is RBAC based**, this will be the Key Vault Secrets User role

```
az role assignment create --role "Key Vault Secrets User" --assignee <KeyVaultManagedIdentityObjectID> --scope <KeyVaultResourceID>
```

**If key vault is policy based**, these will be "GET" policies for secrets, keys and permissions

```
az keyvault set-policy -n <KeyVault> --subscription <KeyVaultSubscriptionID> --secret-permissions get --object-id <KeyVaultManagedIdentityObjectID> --query id
az keyvault set-policy -n <KeyVault> --subscription <KeyVaultSubscriptionID> --key-permissions get --object-id <KeyVaultManagedIdentityObjectID> --query id
az keyvault set-policy -n <KeyVault> --subscription <KeyVaultSubscriptionID> --certificate-permissions get --object-id <KeyVaultManagedIdentityObjectID> --query id
```

## Establish Ingress

Create the kubernetes-internal load balancer and establish ingress to the cluster.

### Get Helm Chart Repository

```
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
```

### Get Profisee's nginxSettings.yaml

```
curl -o nginxSettings.yaml https://raw.githubusercontent.com/profisee/kubernetes/master/Azure-ARM/nginxSettings.yaml
```

### Helm Install Nginx

*You will need to designate an IP from your AKS subnet to be used by nginx for the frontend IP of the load balancer. Make sure to update your firewall or firewall equivalent device to allow inbound HTTPS traffic to this IP.*

```
helm install -n profisee nginx ingress-nginx/ingress-nginx --values nginxSettings.yaml --set controller.service.appProtocol=false --set controller.service.loadBalancerIP= --set controller.service.annotations."service\.beta\.kubernetes\.io/azure-load-balancer-internal"=true
```

### Let's Encrypt Certificate Setup (Optional)

*If you are looking to deploy using a Let's Encrypt certificate instead of an internal certificate (for example, when deploying a POC/POT) you will need to perform the following steps.*

```
helm repo add jetstack https://charts.jetstack.io
helm repo update
helm install cert-manager jetstack/cert-manager -n profisee --set crds.enabled=true --set nodeSelector."kubernetes\.io/os"=linux --set webhook.nodeSelector."kubernetes\.io/os"=linux --set cainjector.nodeSelector."kubernetes\.io/os"=linux --set startupapicheck.nodeSelector."kubernetes\.io/os"=linux
```

### Next Step

[Installing Profisee Software](https://support.profisee.com/wikis/profiseeplatform/installing_profisee_software)