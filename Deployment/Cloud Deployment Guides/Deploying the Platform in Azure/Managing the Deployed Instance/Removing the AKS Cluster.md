# Removing the AKS Cluster

During the deployment or maintenance process, you may encounter a scenario where you need to completely de-provision an AKS cluster that is no longer needed in your environment. For example, if your environment has moved all resources to a new AKS cluster, the old one should be de-provisioned to reduce operating costs. Similarly, if an error occurs during deployment and you are re-attempting the process with a new cluster, the old cluster should be removed.

Deleting the entire Resource Group will de-provision the cluster, but there may be other resources within that Resource Group that you wish to retain. To remove your cluster without deleting the entire Resource Group:

1. Navigate to your [Azure portal](https://portal.azure.com/#home) and select **Resource Groups**from the**Azure Services**options.
2. Navigate to the Resource Group containing the cluster you want to remove.
3. Select the AKS Cluster from the resource list. This resource is labeled with the **Kubernetes service** resource type.
4. Click **Delete** from the toolbar at the top of the screen.![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i5add726097453602.png)

Note that even though this process avoids deleting the resource group containing the cluster, deleting the cluster will necessarily remove the infrastructure resource group that is created with the cluster. This cluster is named **MC\_OriginalResourceGroup\_[ClusterName]\_[location]**and contains the infrastructure resource.