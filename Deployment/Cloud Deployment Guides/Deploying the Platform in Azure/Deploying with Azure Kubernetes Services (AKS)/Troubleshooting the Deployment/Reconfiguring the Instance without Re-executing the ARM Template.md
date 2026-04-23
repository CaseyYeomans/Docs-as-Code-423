# Reconfiguring the Instance without Re-executing the ARM Template

After submitting the ARM template, you may encounter errors during the deployment phase that necessitate re-deploying the instance. Sometimes these errors are caused by Azure-related issues, and no properties of the ARM template need to be changed. In these cases, you can quickly redeploy the Profisee instance without needing to manually complete the ARM template again.

1. Open **Cloud Shell** and connect to the AKS cluster.![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-ica234581e4e5f17.png)
2. Run the following command to configure **kubectl**(Kubernetes control) to allow the kubectl executable to communicate with the cluster.
- ```
az aks get-credentials --resource-group MyResourceGroup --name MyAKSCluster --overwrite-existing
```
3. Run one of the following commands to view information about the nodes, pods, and services within the cluster. **Get all** returns only summary-level information, while **describe all** returns detailed information.
- ```
kubectl get all -OR- kubectl describe all
```
4. Run the following command to check the status of the pod and ensure that it has finished downloading and has started without errors. The download should begin after the ARM template has been submitted.
- ```
kubectl describe pod profisee-0
```
5. Connect to Powershell within the container.
- ```
kubectl exec -it profisee-0 powershell
```
6. Run setup.
- ```
./Setup.ps1
```

After these commands have been run, you can monitor your deployment progress by clicking the **Deployment in progress...** notification in the Azure portal. When the deployment steps begin to succeed, your instance has restarted and will begin to attempt deployment again.