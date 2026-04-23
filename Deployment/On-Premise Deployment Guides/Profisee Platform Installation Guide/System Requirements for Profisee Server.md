# System Requirements for Profisee Server

### Preparing your Application Server for Profisee Platform

Perform the following steps to prepare your server for Profisee installation:

1. Provision a Virtual Machine based on the [Hardware Sizing Guide](https://support.profisee.com/wikis/profiseeplatform/Hardware_Requirements_for_Profisee_Platform). For Azure VMs D-Series and E-Series VMs are recommended.

2. For Cloud VMs create an Azure App Registration for Profisee in Entra **OR** join the OnPrem VM to the Domain and AD

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-icdcd0c7818c1e6a9.png)

3. Create an AD service account with **Allow Interactive Logon** to the Application Server and **Run as Service** permissions

4. Generate a SSL Certificate for the preferred name of the server from a Private or Public CA

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iffde13e4e6bb69ba.png)

5. Run the following PowerShell script (as Administrator) to install the required IIS roles and .Net features.

```
Install-WindowsFeature NET-Framework-45-Features, NET-WCF-Services45, Web-WebServer, Web-Request-Monitor, Web-Dyn-Compression, Web-Basic-Auth, Web-Windows-Auth, Web-App-Dev, Web-Net-Ext, Web-Net-Ext45, Web-Asp-Net, Web-Asp-Net45, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Mgmt-Console, WAS, Web-AppInit
```

6. Check the **Apps & Features** and **Roles and Feature** screens for correct values. Manually add the following Roles and Features if not added by Powershell script

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i963798728442b322.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibac531bb8900fa9.png)

7. Install the latest available version for .NET 8.0.x Windows "Hosting Bundle" and Windows "x64 Desktop Runtime" - <https://dotnet.microsoft.com/en-us/download/dotnet/8.0>

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-if1841b44d6ba0a83.png)

The 8.0.x Windows "Hosting Bundle" includes the Server Hosting and x86 and x64 runtimes. Check Apps and Features to make sure all components are installed.

8. Configure the SSL Certificate in HTTPS Binding in IIS

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5a67bf82553bc78d.png)

### Preparing your SQL Server for Profisee Platform

Perform the following steps to prepare your SQL Server for Profisee installation:

1. Provision a SQL Server DB based on the [Hardware Sizing Guide](https://support.profisee.com/wikis/profiseeplatform/Hardware_Requirements_for_Profisee_Platform). Choose one option based on where your VM is hosted:
1. OnPrem SQL Server 2017 or later - Standard or Enterprise Edition
2. Azure SQL - SQL DB, MI or Elastic Pool - vCore Tier is required with Provisioned General Purpose, Hyperscale or Business Critical Recommended.
3. Amazon RDS
4. Google Cloud SQL

2. Get the SA/SQL Admin Username and Password for the SQL Server (only required during Configuration). For Azure/Amazon/Google SQL Server only SQL Authentication can be used.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibdc3cdbe32430b9c.png)

### Preparing your File Repository for Profisee Platform

A folder on a redundant network storage device is recommended for the Profisee File Repository. The folder should be accessible from all Cluster Nodes (Application Servers) and the Service Account should have Read/Write permissions to the folder.

Alternatively, the folder for the Profisee File Repository can be configured on the local storage drive of the Application Server. This option should only be used when configuring a Single Node Cluster.

For Cloud deployments where only OIDC is used then Cloud Storage Account with a file share should be configured.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-icbf10adcb45cefc0.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ia47e15c098c2bb37.png)