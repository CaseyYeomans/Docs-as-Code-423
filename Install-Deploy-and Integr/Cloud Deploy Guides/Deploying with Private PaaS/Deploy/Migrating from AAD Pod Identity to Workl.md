# Migrating from AAD Pod Identity to Workload Identity

If you are running an older deployment of Profisee, the deployment was likely installed using Azure AD pod-managed identity. AAD pod-managed identity was an AKS feature used to associate managed identities with Kubernetes pods. It is now deprecated (see <https://learn.microsoft.com/en-us/azure/aks/use-azure-ad-pod-identity>). Instead, Microsoft suggests that customers migrate to Microsoft Entra Workload ID (see <https://learn.microsoft.com/en-us/azure/aks/workload-identity-overview>). If you have deployed Profisee after September 2023, you do not have to migrate, as your instance has been deployed using the Workload identity as default. Otherwise, follow the steps below.

1. Register the Workload Identity feature.

```
$RESOURCEGROUPNAME=<ResourceGroupName>

$CLUSTERNAME=<AKSClusterName>

az aks get-credentials --resource-group $RESOURCEGROUPNAME --name $CLUSTERNAME --overwrite-existing;
```

Once workload identity is registered, update the cluster to enable and install it.

```
az aks update -g $RESOURCEGROUPNAME -n $CLUSTERNAME --enable-oidc-issuer --enable-workload-identity
```

2. Get the OIDC Issuer URL and establish a federated identity credential for the managed identity that is used to connect with the Key Vault.

*Note:* if you did not deploy Profisee through the ARM template and instead configured everything manually, your managed identity may be named something other than "AKSKeyVaultUser." To check, find the managed identity in the Infrastructure resource group that has GET permissions or a Key Vault Secrets User role on your Key Vault.

```
$OIDC_ISSUER="$(az aks show -n $CLUSTERNAME -g $RESOURCEGROUPNAME --query "oidcIssuerProfile.issuerUrl" -o tsv)"

$identityName="AKSKeyVaultUser"

$AKSINFRARESOURCEGROUPNAME ="$(az aks show -n $CLUSTERNAME -g $RESOURCEGROUPNAME --query "nodeResourceGroup" -o tsv)

az identity federated-credential create --name ProfiseefederatedId --identity-name $identityName --resource-group $AKSINFRARESOURCEGROUPNAME --issuer $OIDC_ISSUER --subject system:serviceaccount:profisee:profiseeserviceaccount --audience api://AzureADTokenExchange
```

3. Obtain the Profisee values using the command.

```
helm get values -n profisee profiseeplatform -o yaml > Settings.yaml

helm repo update profisee

helm -install upgrade profiseeplatform profisee/profisee-platform --values Settings.yaml -n profisee
```

4. The Profisee pod and the Key Vault pod will automatically delete themselves and start running again after the helm install.
5. AAD Pod Identity is no longer required. Uninstall it by using command below:

```
helm uninstall pod-identity -n profisee
```

6. As a sanity check, after uninstalling the pod identity, delete *profisee-keyvault* and *profisee-0* pods to make sure that they can spin up correctly after the migration.