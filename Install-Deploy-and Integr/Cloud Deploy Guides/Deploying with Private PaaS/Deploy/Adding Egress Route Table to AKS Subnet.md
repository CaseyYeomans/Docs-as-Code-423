# Adding Egress Route Table to AKS Subnet

To facilitate fully private egress from the cluster to a next hop appliance, a route table needs to be created and associated with the AKS subnet **before** AKS is deployed in it.

See: <https://docs.microsoft.com/en-us/azure/aks/limit-egress-traffic>

| | |
| --- | --- |
| **Route Table Setting** | **Value** |
| Address Prefix | 0.0.0.0/0 |
| Next hop type | Virtual Appliance |
| Next hop IP address | The IP of the egress device--you must make sure that this "next hop" device or service will have enough outbound IPs to prevent [SNAT exhaustion](https://docs.microsoft.com/en-us/azure/load-balancer/load-balancer-outbound-connections). For example, if you use Azure Firewall (which scales up to 20 IPs) this would be the firewall's internal IP. |

### Create Azure Firewall

Azure documentation for: [az network firewall](https://docs.microsoft.com/en-us/cli/azure/network/firewall?view=azure-cli-latest), [az network public-ip](https://docs.microsoft.com/en-us/cli/azure/network/public-ip?view=azure-cli-latest), [az network firewall ip-config](https://profisee1-my.sharepoint.com/personal/brynn_lewis_profisee_com/Documents/BrynnLe/Documents/az network firewall ip-config)

As previously mentioned, this example uses Azure Firewall as a sample "next hop" appliance for AKS. If using Azure Firewall, modify as appropriate to your security needs.

```
az network firewall create -l <region> -n <AzureFirewall> -g <AppResourceGroup>
az network public-ip create -l <region> -n <AzureFirewall-pip> -g <AppResourceGroup> --allocation-method static --sku standard
az network firewall ip-config create -n FW-config -g <AppResourceGroup> --firewall-name <AzureFirewall> --public-ip-address <AzureFirewall-pip> --vnet-name <HubVirtualNetwork>
az network firewall update -n <AzureFirewall> -g <AppResourceGroup>
```

### Create Route Table and Add Route

Azure documentation for: [az network route-table](https://docs.microsoft.com/en-us/cli/azure/network/route-table?view=azure-cli-latest), [az network route-table route](https://docs.microsoft.com/en-us/cli/azure/network/route-table/route?view=azure-cli-latest)

```
az network route-table create -n <AKSRouteTable> -g <AppResourceGroup>
az network route-table route create -n <AKSEgressRoute> -g <AppResourceGroup> --route-table-name <AKSRouteTable> --next-hop-type VirtualAppliance --address-prefix 0.0.0.0/0 --next-hop-ip-address <AppliancePrivateIP>
```

### Associate Route Table with AKS Subnet

Azure documentation for: [az network vnet subnet](https://docs.microsoft.com/en-us/cli/azure/network/vnet/subnet?view=azure-cli-latest)

```
az network vnet subnet update -n <AKSSubnet> -g <AppResourceGroup> --vnet-name <SpokeVirtualNetwork> --route-table <AKSRouteTable>
```

### Next Step

[Setup for Private PaaS Deployment](https://support.profisee.com/wikis/profiseeplatform/setup_for_private_paas_deployment)