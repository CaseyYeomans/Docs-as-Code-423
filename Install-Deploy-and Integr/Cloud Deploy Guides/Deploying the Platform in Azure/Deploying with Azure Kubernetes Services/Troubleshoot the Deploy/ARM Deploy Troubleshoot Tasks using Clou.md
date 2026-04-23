# ARM Deployment Troubleshooting Tasks using Cloud Shell

If the ARM deployment fails without an explicit error message, or if the deployment seems as if it should have been successful but was not, you should manually check for errors within Cloud Shell. Cloud Shell is a function of the Azure portal and can be selected from the toolbar on the top-right of the deployment page. Cloud Shell can interact directly with Azure Kubernetes Services and is highly recommended for troubleshooting AKS errors.

### Accessing the Configuration Manager Error Log using Cloud Shell

1. Open Cloud Shell and connect to the AKS cluster.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i790e100f7780f223.png)
2. Run the following command to configure **kubectl**(Kubernetes control) to allow the kubectl executable to communicate with the cluster.
- ```
az aks get-credentials --resource-group [Resource Group Name] --name [AKS Cluster Name] --overwrite-existing
```
3. Run one of the following commands to view information about the nodes, pods, and services within the cluster. The **get all** command returns only summary-level information, while **describe all** returns detailed information.
- ```
kubectl --namespace profisee get all -OR- kubectl describe all
```
4. Run the following command to check the status of the pod and ensure that it has finished downloading and has started without errors. The download should begin after the ARM template has been submitted.
- ```
kubectl --namespace profisee describe pod profisee-0
```
5. Connect to Powershell within the container.
- ```
kubectl --namespace profisee exec -it profisee-0 powershell
```
6. Within Powershell on the container, check the configuration manager log using the following command. This log contains information about what happened during the execution of the Configuration Manager during container startup.
- ```
Get-Content C:\Profisee\Configuration\LogFiles\SystemLog.log
```
7. Check for errors.

Depending on the errors encountered, you may need to use Helm to uninstall and reinstall Profisee. For more information, see [Uninstalling and Reinstalling using Helm](https://support.profisee.com/wikis/profiseeplatform/uninstalling_and_reinstalling_using_helm).

### General Troubleshooting Tasks

The following explains how to perform common troubleshooting tasks using Cloud Shell.

- **Open Cloud Shell and connect to the AKS cluster.**
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i4f380e8217758101.png)
- **Inspect information about the application pools used in the Profisee node.**

You can view and manage the Profisee Windows service by running one of the following commands. In this instance, the service name is **Profisee**.

```
Get-service Profisee -OR- Restart-Service Profisee
```

You can also get information about app pools by running the following command.

```
Get-IISAppPool
```

- **Check the SQL connection from the container.**

Note that the User ID and Password must match the credentials the container will use.

```
$connectionString = 'Data Source={0};database={1};User ID={2};Password={3}' -f $env:ProfiseeSqlServer,$env:ProfiseeSqlDatabase,$env:ProfiseeSqlUserName,$env:ProfiseeSqlPassword
$sqlConnection = New-Object System.Data.SqlClient.SqlConnection $connectionString
$sqlConnection.Open()
$sqlConnection.Close()
```

- **Check the connection to the Profisee file repository (file share).**

```
$pass=$env:ProfiseeAttachmentRepositoryUserPassword|ConvertTo-SecureString -AsPlainText -Force
$azureCredential = New-Object System.Management.Automation.PsCredential($env:ProfiseeAttachmentRepositoryUserName,$pass)
New-PSDrive -Name "[Drive]" -PSProvider "FileSystem" -Root $env:ProfiseeAttachmentRepositoryLocation -Credential $azureCredential -Persist;
#remove mapped drive
Remove-PSDrive [Drive]
```

- **Get the cluster's inbound IP.**

```
kubectl --namespace profisee describe services nginx-nginx-ingress-controller
```

- **Copy a file to the container.**

```
kubectl --namespace profisee cp [file name] profisee-0:[file path]
```

- **Test connectivity between two nodes.**

If you have more than one pod, you can use this to test if they are communicating with each other. If successful, an http 200 will be returned. The following command can be used from a pod other than profisee-1 (e.g. profisee-0) to see if it can communicate with profisee-1, but no more than 2 nodes are supported at a time.

```
curl http:/profiseeplatform/profisee-1/profisee/api/service.svc -usebasicparsing
```