# Configuring Private DNS Zones

Private DNS Zones must be created for the Private Endpoints. The Private DNS Zones must be peered to the virtual networks for DNS resolution.

| | | |
| --- | --- | --- |
| **Type** | **Zone** | **Use** |
| Storage Account | privatelink.file.core.windows.net | Mandatory |
| SQL | privatelink.database.windows.net | Mandatory |
| AKS Cluster | privatelink.<region>.azmk8s.io | Mandatory |
| Key Vault | privatelink.vaultcore.azure.net | Optional |
| Private Purview | privatelink.purview.azure.com | Optional |

See: [https://docs.microsoft.com/en-us/azure/private-link/private-endpoint-dns](https://docs.microsoft.com/en-us/azure/private-link/private-endpoint-dns )

### Create Private DNS Zones for Storage Accounts, SQL, AKS, Key Vault, and Purview

Azure documentation for: [az network private-dns](https://docs.microsoft.com/en-us/cli/azure/network/private-dns?view=azure-cli-latest)

```
az network private-dns zone create -n privatelink.file.core.windows.net -g <AppResourceGroup>
az network private-dns zone create -n privatelink.database.windows.net -g <AppResourceGroup>
az network private-dns zone create -n privatelink.<region>.azmk8s.io -g <AppResourceGroup>
az network private-dns zone create -n privatelink.vaultcore.azure.net -g <AppResourceGroup>
az network private-dns zone create -n privatelink.purview.azure.com -g <AppResourceGroup>
```

### Add Virtual Links for Private DNS Zones

Azure documentation for: [az network private-dns link vnet](https://profisee1-my.sharepoint.com/personal/brynn_lewis_profisee_com/Documents/BrynnLe/Documents/Az network https:/docs.microsoft.com/en-us/cli/azure/network/private-dns/link/vnet?view=azure-cli-latest)

```
az network private-dns link vnet create -n <StoragetoSpokeDNSLink> -g <AppResourceGroup> -z privatelink.file.core.windows.net -v <SpokeVirtualNetwork> --registration-enabled false
az network private-dns link vnet create -n <SQLtoSpokeDNSLink> -g <AppResourceGroup> -z privatelink.database.windows.net -v <SpokeVirtualNetwork> --registration-enabled false
az network private-dns link vnet create -n <AKStoSpokeDNSLink> -g <AppResourceGroup> -z privatelink.<region>.azmk8s.io -v <SpokeVirtualNetwork> --registration-enabled false
```

**Repeat for Purview and Key Vault DNS Zones described in table above if using.**

### Next Step

[Adding Egress Route Table to AKS Subnet](https://support.profisee.com/wikis/profiseeplatform/adding_egress_route_table_to_aks_subnet)