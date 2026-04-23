# Private PaaS Deployment Overview

This document is a guide to deploying Profisee within an AKS cluster with a private API that does not use or expose any public IPs. As every customer's environment is unique, we acknowledge that some of these steps may need to be modified to work with your network topology or security requirements. Our approach is based on Azure documentation and, where relevant, we have included external links for context. Our standard installation is based on a hub and spoke network topology with Azure Firewall described here (<https://learn.microsoft.com/en-us/azure/architecture/example-scenario/aks-firewall/aks-firewall>) but the exact configuration is open to customer variation.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i96bb1ce26848351f.png)

- **Azure Kubernetes Services**: The AKS deployment will have a Windows node pool (to run Profisee) and a Linux node pool (to run everything else), for that purpose we will be using the Azure CNI plugin.
- **Firewall**: Traffic from AKS will be routed out through an appliance, in this configuration we are using Azure Firewall.
- **Jumpbox**: Private AKS clusters are deployed without a public IP address. Instead, you will manage AKS and deploy Profisee using a virtual machine that has access to the AKS virtual network. We create a jumpbox in a subnet within the same network as our AKS cluster for this purpose.
- **Kubernetes Internal Load Balancer**: To prevent AKS from automatically generating a load balancer with a public IP to be used for egress, we will set up a route table and use [User-Defined Routing](https://docs.microsoft.com/en-us/azure/aks/egress-outboundtype) to reach the "next hop" IP in your network.
- **Private DNS Zones and Records**: Private endpoint records will be registered in a [corresponding private DNS zone](https://docs.microsoft.com/en-us/azure/private-link/private-endpoint-dns#azure-services-dns-zone-configuration), for correct DNS resolution between various resources. This works by establishing virtual network links between the DNS zone and the virtual networks where DNS resolution needs to take place.
- **Private Endpoints**: Private endpoints are used to connect different resources via Microsoft's backbone network. They are special network interfaces (NICs) for Azure services that use private IP addresses.
- **Azure SQL**: Profisee utilizes SQL as a database. SQL needs to be configured with a private endpoint for completely private networking.
- **Storage Account**: The storage account is used to hold a mixture of file attachments, configurations files, and workflow definitions. It needs to be configured with a private endpoint and public access denied for completely private networking.
- **Purview**: We allow integration with Microsoft Purview for data governance. If you wish to use Microsoft Purview with completely private networking, you will need to configure a private endpoint to connect to Purview and deny public access.
- **Key Vault**: We allow integration with Key Vault if you wish to use secrets stored in a vault rather than inputting them manually. You will need to configure a private endpoint to connect to it for completely private networking.
- **Virtual Networks**: For the sake of this tutorial, we have created several peered virtual networks to provide logical divisions between different resources. You may configure your VNets and networking as appropriate to your environment, providing you allocate sufficient address space.

### Next Step

[Deployment Steps](https://support.profisee.com/wikis/profiseeplatform/deployment_steps)