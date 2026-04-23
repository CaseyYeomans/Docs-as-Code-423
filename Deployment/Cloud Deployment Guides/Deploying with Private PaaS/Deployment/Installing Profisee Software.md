# Installing Profisee Software

Now that the infrastructure has been deployed, the final step is to install Profisee in the AKS cluster.

### Set Up OIDC Provider

In order to correctly authenticate you will need to set up your OIDC provider. In Azure, this will involve setting up an app registration for redirects. Refer to existing Profisee documentation around [OIDC](https://support.profisee.com/wikis/profiseeplatform/oidc_provider_info_and_claims_mappings).

### Set Up Profisee File Share for Storage Account

Azure documentation for: [az storage share](https://docs.microsoft.com/en-us/cli/azure/storage/share?view=azure-cli-latest)

```
az storage share create -n <FileShareName> --account-key <StorageAccountAccessKey> --account-name <StorageAccount>
```

### Get Profisee's Settings.yaml file

```
curl -o Settings.yaml https://raw.githubusercontent.com/profisee/kubernetes/master/Azure-ARM/Settings.yaml
```

### Update Settings.yaml

Configure the Settings.yaml file with the values specific to your Profisee installation. Save the file. If you have configured your environment to use a Key Vault, you can store the license, the SQL Username and Password as secrets, and your own TLS Certificate as a Key Vault certificate. As you are editing this manually, you will have to request the ACR credentials and auth token from Profisee Support.

| | |
| --- | --- |
| **Value** | **Meaning** |
| sqlServer: name | FQDN of the SQL server, ex. <server>.database.windows.net |
| sqlServer: databaseName | Name of the database |
| sqlServer: userName | SQL username or name of key vault secret containing SQL username |
| sqlServer: password | SQL password or name of key vault secret containing SQL password |
| profiseeRunTime: useLetsEncrypt | Boolean value: *true* if you want to use Let's Encrypt to generate a certificate, *false* if you want to use your own certificate |
| profiseeRunTime: adminAccount | Email of the super admin that will be created as the first user in the Profisee database |
| profiseeRunTime: fileRepository: accountName | Name of the storage account, excluding the .file.core.windows.net part |
| profiseeRunTime: fileRepository: userName | Use "Azure\\<accountName>" |
| profiseeRunTime: fileRepository: password | Storage account access key |
| profiseeRunTime: fileRepository: logonType | Default value NewCredentials (do not change) |
| profiseeRunTime: fileRepository: location | Use "\\\\<accountName>.file.core.windows.net\\<fileShareName>" |
| profiseeRunTime: fileRepository: fileShareName | Name of the file share created in the storage account |
| profiseeRunTime: externalDnsURL | Use "https://<externalDnsName>" Profisee binds licenses to FQDNs so make sure this matches the FQDN that you requested from Support. |
| profiseeRunTime: externalDnsName | Must match the externalDnsURL, minus the https:// prefix. |
| profiseeRunTime: webAppName | Web App name. We support alternatives, but a good default name is "profisee." |
| profiseeRunTime: deployIngressRule | Boolean value: default *true* deploys nginx ingress rule (do not change). |
| profiseeRunTime: isPaaS | Boolean value: default *true* (do not change) |
| profiseeRunTime: oidc: name | Default "Azure Active Directory." Can be customized to anything you like, not visible. |
| profiseeRunTime: oidc: authority | For Azure Active Directory use https://login.microsoftonline.com/<tenantID>, we also support Okta and Google, as well as multiple OIDC providers simultaneously. |
| profiseeRunTime: oidc: clientId | App registration client Id. |
| profiseeRunTime: oidc: clientSecret | App registration secret value (optional) |
| profiseeRunTime: oidc: usernameClaim | *Default claim for Azure Active Directory:* "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" *Default claim for Okta:* "<PreferredUsername>" *Default claim for Google:* "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress" |
| profiseeRunTime: oidc: userIdClaim | *Default claim for Azure Active Directory:* "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier" *Default claim for Okta:* "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier" *Default claim for Google:* "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier" |
| profiseeRunTime: oidc: firstNameClaim | *Default claim for Azure Active Directory:* "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" *Default claim for Okta:* "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" *Default claim for Google:* "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" |
| profiseeRunTime: oidc: lastNameClaim | *Default claim for Azure Active Directory:* "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" *Default claim for Okta:* "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" *Default claim for Google:* "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" |
| profiseeRunTime: oidc: emailClaim | *Default claim for Azure Active Directory* "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" *Default claim for Okta:* "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress" *Default claim for Google:* "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress" |
| profiseeRunTime: clusterNodeCount | Node count will depend on the type of license purchased. Default value is 1 for a single server. |
| clusterNode: limits: cpu | Maximum number of cores that Profisee will use. See chart below. |
| clusterNode: limits: memory | Maximum amount of memory that Profisee will use. See chart below. |
| clusterNode: requests: cpu | Amount of CPU initially requested by the container, default is 1 core |
| clusterNode: requests: memory | Amount of memory initially requested by container, default is 1000M |
| image: registry | Profisee's container repository, use profisee.azurecr.io |
| image: repository | Name of Profisee's repository profiseeplatform |
| image: tag | Version of Profisee's software used, should match whatever is in your license, format: YYYYrX.X, ex. 2022r1.0 |
| image: auth | *JSON formatted values* username: provided by Profisee password: provided by Profisee email: support@profisee.com auth: provided by Profisee |
| licenseFileData | Base64 encoded string copied from license file without surrounding quotations **or** name of key vault secret containing license file |
| preInitScriptData | Base64 encoded version of any PowerShell command to run before the actual configuration process starts. |
| postInitScriptData | Base64 encoded version of any PowerShell commands to run after the configuration process ends. |
| oidcFileData | If using multiple OIDC providers, put JSON for additional providers here. Profisee can provide a sample file. |
| tlsCert | Option 1: Certificate value, JSON formatted using 4 spaces in front of every line. Must include the ----BEGIN CERTIFICATE---- and ----END CERTIFICATE---- header and footer. Option 2: Name of certificate stored in key vault Option 3: NA (if using Let's Encrypt). |
| tlsKey | Option 1: Certificate private key value, JSON formatted using 4 spaces in front of every line. Must include the ----BEGIN PRIVATE KEY---- and ----END PRIVATE KEY---- header and footer Option 2: Name of certificate stored in key vault. Option 3: NA (if using Let's Encrypt). |
| cloud: azure: isProvider | Boolean value: default *true*, leave true for Azure |
|