# Planning Your Cluster and Network Requirements

There are a few considerations and potential prerequisite steps that you must plan for before deploying your Profisee AKS cluster. The diagram below illustrates the basic planning steps you perform before starting the deployment process.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i48f778c7f80fe26.png)

### Choosing Your Cluster Name

Each AKS cluster must be given a name. Profisee's ARM template defaults this to **MyAKSCluster** in the **Kubernetes Cluster Name** property. However, you can choose a different name provided it follows the rules below. Record this name for reference when executing the actual deployment.

- The name must be unique within cluster's Resource Group.
- The name may only contain letters, numbers, underscores, and hyphens.
- The name must start and end with only letters or numbers (no underscores or hyphens)

### Choosing Virtual Machine (VM) Sizes

The Profisee AKS cluster contains 2 [Node Pools](https://support.profisee.com/wikis/profiseeplatform/glossary_of_azure_and_aks_terms), each of which is supported by a Virtual Machine (VM). The ARM template allows you to specify the size of each of these VMs in following ARM template properties:

- **Kubernetes Linux VM Size**
- **Kubernetes Windows VM Size**

The Linux VM is used primarily for provisioning and management of the cluster and, thus, does not have significant resource needs. The Windows VM, on the other hand, runs the application workloads of the Profisee Platform. As such, the size of this VM should be set according to the anticipated workload and data volumes you plan to address on this specific cluster instance. You should consult your Azure infrastructure administrators along with your Profisee Professional Services and/or Support contacts in properly sizing the Windows VM size. Once you have determined both, you should record these values for use when [Deploying the AKS Cluster using the ARM Template](https://support.profisee.com/wikis/profiseeplatform/deploying_the_AKS_cluster_with_the_arm_template). Refer to [Sizes for virtual machines in Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/sizes) on the Microsoft documentation web site for more details on virtual machine types, sizes, and costs.

### Choosing the Kubernetes Version

The ARM template allows you to target a specific Kubernetes version for your Profisee cluster. Unless you have a reason to target a specific version (e.g. you are aware of known issues or limitations in the default version), Profisee recommends you use the default version available in the target Azure regional data center. Choose the default version by leaving the **Kubernetes Version** property blank during the ARM template deployment.

If you want to target a specific Kubernetes version, this can be specified manually. To determine what versions are supported in your Azure location, refer to [Supported Kubernetes versions in Azure Kubernetes Service (AKS)](https://docs.microsoft.com/en-us/azure/aks/supported-kubernetes-versions) or use the following Azure CLI command:

```
az aks get-versions --location [location] --output table
```

You must specify the version in the exact [major].[minor].[patch] format detailed in [Supported Kubernetes versions in Azure Kubernetes Service (AKS)](https://docs.microsoft.com/en-us/azure/aks/supported-kubernetes-versions).

### Advance Networking Considerations

Profisee's deployment process will provision a new VNet automatically as part of the deployment process. This network configuration is sufficient for most deployments. However, if you have advanced networking needs and considerations, you can associate a Profisee cluster with an existing VNet, or you can provision your VNet in advance and tailor it to your corporate infrastructure needs before associating this VNet with the Profisee cluster.

You make the choice to use and existing VNet by specify the following ARM template properties:

- **Kubernetes Vnet Name**
- **Kubernetes Vnet Resource Group**

**If these are specified, then you must:**

- Create or obtain the Subnet name you want to associate with the resources provisioned for the cluster. This is specified in the ARM template via the **Kubernetes Subnet Name**.
- Identify the network address range that is associated with the Virtual Machines within the specified Subnet. This is specified in the ARM template via the **Kubernetes Service Cidr** property.
- Identify the DNS Service IP address that will support name resolution within the cluster. This is specified in the **Kubernetes DNS Service IP** property.
- Identify the internal network address range used by the pods (containers) within the cluster. This is specified via the **Kubernetes Docker Bridge Cidr** property.

CIDR stands for Classless Inter-Domain Routing. [CIDR notation](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#CIDR_notation) provides a compact way of representing an IP address range. Both the **Kubernetes Service Cidr** and **Kubernetes Docker Bridge Cidr** are specified in CIDR notation.

If you leave both the Kubernetes Vnet Name and Kubernetes Vnet Resource Group properties black, you are telling the Profisee AKS deployment process that you want a new dedicated VNet create for this cluster and all of the other related properties referenced above are ignored.

### Wrapping Up Cluster & Network Planning

As part of this planning process, you should now have identified the following properties of the Profisee ARM template:

- Kubernetes Cluster Name
- Kubernetes Linus VM Size
- Kubernetes Windows VM Size
- Kubernetes Vnet Name
- Kubernetes Vnet Resource Group
- Kubernetes Subnet Name
- Kubernetes Service Cidr
- Kubernetes DNS Service IP
- Kubernetes Docker Bridge Cidr

You may now continue to [Obtaining Your Profisee License and Container Registry Credentials](https://support.profisee.com/wikis/profiseeplatform/obtaining_your_profisee_license_and_container_registry_credentials) or return to [Planning Your Deployment](https://support.profisee.com/wikis/profiseeplatform/deploying_profisee_using_the_arm_template).

### See more

- [Planning Your AKS ARM Deployment](https://support.profisee.com/wikis/profiseeplatform/deploying_profisee_using_the_arm_template)
- [Deploying the AKS Cluster using the ARM Template](https://support.profisee.com/wikis/profiseeplatform/deploying_the_AKS_cluster_with_the_arm_template)