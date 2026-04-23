# Uninstalling and Reinstalling using Helm

When troubleshooting for errors, you may encounter critical errors that require you to uninstall and reinstall Profisee. This can be done using [Helm](https://helm.sh/docs/), a package manager for Azure Kubernetes Services. Helm is built into Cloud Shell services and does not require external installation.

You will also need the **Settings.yaml**file located in your generated storage account. You can download your Settings.yaml file from your storage account, then upload itto the Cloud Shell drive and redeploy.

1. Download **Settings.yaml** from your generated storage account
1. Click the generated storage account within your Resource Group, then select **File shares**, then select the generated file share name, then select **azscriptinput**.
2. Click **Settings.yaml**, then download.

Note: The generated storage account is separate from the storage account you manually create. This storage account and its name is automatically generated and appears in the same resource group.

1. Edit the **Settings.yaml** file and adjust any of the ARM template properties if needed. For details on the ARM template properties, see [Deploying the AKS Cluster using the ARM Template](https://support.profisee.com/wikis/profiseeplatform/deploying_the_AKS_cluster_with_the_arm_template).
2. Upload the **Settings.yaml** file to the Cloud Shell drive.
1. Select the Upload/Download file button in the menu
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i96e08a37455eb78e.png)
2. Click **Upload**
3. Select the **Settings.yaml** you previously downloaded, then select **Open**.
4. Wait for the upload to complete. Progress is displayed on the bottom right of the shell window.
3. View the uploaded file using the following command to ensure everything appears correct.

- ```
cat ./Settings.yaml
```

5. Exit the container using the following command.

- ```
exit
```

6. Uninstall and reinstall Profisee using the following commands.

- ```
helm repo add profisee https://profisee.github.io/kubernetes
helm uninstall profiseeplatform2020r1
helm install profiseeplatform2020r1 profisee/profisee-platform --values Settings.yaml
```

If you are unable to log in and encounter issues with Azure Active Directory API Permissions, ensure the app registration is assigned the proper API permissions. It should be displayed as follows. If not, click **Add a Permission** and adjust your permissions to appear as follows.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic6ef07a7bcf5c659.png)

Note that **Microsoft Graph** is the "read" API for all of Azure and is required.