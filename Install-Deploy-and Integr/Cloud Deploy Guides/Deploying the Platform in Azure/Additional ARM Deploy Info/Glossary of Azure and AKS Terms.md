# Glossary of Azure and AKS Terms

While planning for your AKS deployment, or while completing the ARM template, you may encounter terms that are unique to Azure and Azure Kubernetes Services (AKS). You can refer to the table below for a comprehensive list of Azure and AKS terms relevent to the deployment process.

| | | |
| --- | --- | --- |
| **Term** | **Description** | **See more** |
| **Azure Active Directory** | Azure Active Directory is Microsoft's cloud-based identity and access management service. | <https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-whatis> |
| **Azure Container Registry (ACR)** | Azure Container Registry is a managed, private Docker registry service based on the open-source Docker Registry 2.0. | <https://docs.microsoft.com/en-us/azure/container-registry/container-registry-intro> |
| **Azure Kubernetes Services (AKS)** | Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications. | <https://azure.microsoft.com/en-us/topic/what-is-kubernetes/> |
| **Azure Storage Account** | An Azure storage account contains all of your Azure Storage data objects: blobs, files, queues, tables, and disks. The storage account provides a unique namespace for your Azure Storage data that is accessible from anywhere in the world over HTTP or HTTPS. | <https://docs.microsoft.com/en-us/azure/storage/common/storage-account-overview?toc=/azure/storage/blobs/toc.json> |
| **Helm** | The package manager for Azure Kubernetes Services, necessary for uninstalling and reinstalling Profisee with AKS. | <https://helm.sh/docs/> |
| **Managed Identity** | A Managed Identity manages credentials when authenticating to cloud services. Managed Identities needed for deployment are user-assigned and managed within the Azure portal. | <https://docs.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview> |
| **Node** | The worker machines that run your containerized applications and other workloads. | <https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture#nodes> |
| **Node Pool** | A group of nodes within a cluster that all have the same configuration. | <https://cloud.google.com/kubernetes-engine/docs/concepts/node-pools> |
| **Resource Group** | A Resource Group is a container that holds related resources for an Azure solution. The Resource Group includes the resources you want to manage as a group. | <https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/overview#resource-groups> |
| **SKU Type** | SKU Type refers to a pricing tier for Azure Storage Accounts. For the purposes of deployment, your SKU Type will be input as your Storage Account Type. | <https://docs.microsoft.com/en-us/rest/api/storagerp/srp_sku_types> |

For information on general Azure related terms not related to AKS deployment, refer to [Microsoft's Azure AD Terminology](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-whatis#terminology).