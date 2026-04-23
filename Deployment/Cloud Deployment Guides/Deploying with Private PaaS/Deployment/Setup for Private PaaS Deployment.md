# Setup for Private PaaS Deployment

### Set-Up SQL

Deploy a SQL server and database that are not publicly accessible and create a private endpoint for the SQL server and integrate it with the privatelink.database.windows.net DNS Zone.

### Create SQL Server

Azure documentation for: [az sql server](https://docs.microsoft.com/en-us/cli/azure/sql/server?view=azure-cli-latest)

*If your security requirements necessitate the use of Azure AD, you may use that instead of an admin user and password. Refer to the documentation linked for relevant command.*

```
az sql server create -l <region> -n <ProfiseeSQLServer> -g <AppResourceGroup> --enable-public-network false --admin-user <USERNAME> --admin-password <PASSWORD>
```

### Create SQL Database

Azure documentation for: [az sql db](https://docs.microsoft.com/en-us/cli/azure/sql/server?view=azure-cli-latest)

```
az sql db create -n <ProfiseeDatabase> -g <AppResourceGroup> --server <ProfiseeSQLServer>
```

### Create SQL Private Endpoint

Azure documentation for: [az network private-endpoint](https://docs.microsoft.com/en-us/cli/azure/network/private-endpoint?view=azure-cli-latest), [az network private-endpoint](https://docs.microsoft.com/en-us/cli/azure/network/private-endpoint/dns-zone-group?view=azure-cli-latest), [dns-zone-group](https://docs.microsoft.com/en-us/cli/azure/network/private-endpoint/dns-zone-group?view=azure-cli-latest)

```
az network private-endpoint create -l <region> -n <SQLPrivateEndpoint> -g <AppResourceGroup> --vnet-name <SpokeVirtualNetwork> --subnet <AppSubnet> --private-connection-resource-id <SQLServerResourceID> --connection-name <SQLConnection> --group-id sqlServer
```

```
az network private-endpoint dns-zone-group create -n <SQLZoneGroup> -g <AppResourceGroup> --endpoint-name <SQLPrivateEndpoint> --zone-name <SQLPrivateDNSZone> --private-dns-zone privatelink.database.windows.net
```

## Set-Up Storage Account

Create a storage account that has no public access and create a private endpoint for that storage account and integrate it with the *privatelink.file.core.windows.net* DNS zone.

### Create the Storage Account

Azure documentation for: [az storage account](https://docs.microsoft.com/en-us/cli/azure/storage/account?view=azure-cli-latest#az-storage-account-create)

```
az storage account create -l <region> -n <StorageAccount> -g <AppResourceGroup> --public-network-access Disabled --sku <SKU>
```

### Create Storage Account Private Endpoint

Azure documentation for: [az network private-endpoint](https://docs.microsoft.com/en-us/cli/azure/network/private-endpoint?view=azure-cli-latest), [az network private-endpoint](https://docs.microsoft.com/en-us/cli/azure/network/private-endpoint/dns-zone-group?view=azure-cli-latest), [dns-zone-group](https://docs.microsoft.com/en-us/cli/azure/network/private-endpoint/dns-zone-group?view=azure-cli-latest)

```
az network private-endpoint create -l <region> -n <StoragePrivateEndpoint> -g <AppResourceGroup> --vnet-name <SpokeVirtualNetwork> --subnet <AppSubnet> --private-connection-resource-id <StorageAccountResourceID> --connection-name <StorageConnection> --group-id file
```

```
az network private-endpoint dns-zone-group create -n <StorageZoneGroup> -g <AppResourceGroup> --endpoint-name <StoragePrivateEndpoint> --zone-name <StoragePrivateDNSZone> --private-dns-zone privatelink.file.core.windows.net
```

### Set-Up Connection to Purview (Optional)

Azure documentation for: [az network private-endpoint](https://docs.microsoft.com/en-us/cli/azure/network/private-endpoint?view=azure-cli-latest), [az network private-endpoint dns-zone-group](https://docs.microsoft.com/en-us/cli/azure/network/private-endpoint/dns-zone-group?view=azure-cli-latest)

*Set up a private endpoint for an already existing instance of Microsoft Purview and integrate it with the* privatelink.purview.azure.com *DNS zone.*

```
az network private-endpoint create -l <region> -n <PurviewPrivateEndpoint> -g <AppResourceGroup> --vnet-name <AppVirtualNetwork> --subnet <PurviewSubnet> --private-connection-resource-id <PurviewResourceID> --connection-name <PurviewConnection> --group-id account
```

```
az network private-endpoint dns-zone-group create -n <PurviewZoneGroup> -g <AppResourceGroup> --endpoint-name <PurviewPrivateEndpoint> --zone-name <PurviewPrivateDNSZone> --private-dns-zone privatelink.purview.azure.com
```

### Set-Up Key Vault (Optional)

Azure documentation for: [az network private-endpoint](https://docs.microsoft.com/en-us/cli/azure/network/private-endpoint?view=azure-cli-latest), [az network private-endpoint dns-zone-group](https://docs.microsoft.com/en-us/cli/azure/network/private-endpoint/dns-zone-group?view=azure-cli-latest)

*Set up a private endpoint for an already existing Key Vault and integrate it with the* privatelink.vaultcore.azure.net *DNS zone.*

```
az network private-endpoint create -l <region> -n <KeyVaultPrivateEndpoint> -g <AppResourceGroup> --vnet-name <AppVirtualNetwork> --subnet <KeyVaultSubnet> --private-connection-resource-id <KeyVaultResourceID> --connection-name <KeyVaultConnection> --group-id vault
```

```
az network private-endpoint dns-zone-group create -n <KeyVaultZoneGroup> -g <AppResourceGroup> --endpoint-name <KeyVaultPrivateEndpoint> --zone-name <KeyVaultPrivateDNSZone> --private-dns-zone privatelink.vaultcore.azure.net
```

### Next Step

[Configuring "Next Hop" Ingress and Egress](https://support.profisee.com/wikis/profiseeplatform/configuring_next_hop_ingress_and_egress)