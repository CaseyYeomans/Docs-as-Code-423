# Service Configurations

Once you have enabled at least one Service Provider, you can create a Service Configuration to enable integration. You must create at least one Service Configuration before you can create a connection strategy.

### Add a Service Configuration

To add a new Service Configuration:

1. Navigate to the Service Configurations tab.
2. Click the **+**icon on the Service Provider page.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i6ee2ca452297eb29.png)
3. Click the dropdown selected under Service Provider and select a provider from the list. This list is populated with previously imported [Service Providers](https://support.profisee.com/wikis/profiseeplatform/service_providers).
4. Select a **Service**from the dropdown list. The available services will depend on the Service Provider selected.
5. Select an **Operation**from the dropdown list. The available operations will depend on the Service selected.
6. Provide a name for the Configuration under the **Configuration Name** field.
7. Click **Continue**. The Service Configuration editor is created on the page. If you do not wish to continue editing this configuration, click **Save** or **Save and** **Close**.

### Import or Export a Service Configuration

Instead of manually creating a Service Configuration, you can also import a service configuration by clicking the three-dot icon on the right-hand side of the Service Configurations toolbar, then selecting **Import** and uploading a Service Configuration .JSON file from your device.

You can export a service configuration in the Service Configurations list by clicking the ellipsis icon to the left of the service configuration name and clicking **Export (Selected)** to download the configuration as a .JSON file.

### Edit a Service Configuration

To edit an existing Service Configuration, click the name of a service configuration in the Service Configurations list, or click the ellipsis icon to the left of the name and select **Open**.

From here, three tabs display: **Overview**, **Settings**, and **Headers**.

#### Overview

The **Overview**tab displays the information submitted when adding the service configuration, including the Configuration Name, Service Provider, Service, and Operation. Of these properties, only the Configuration Name can be edited.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i4fcf6c68da70fd13.png)

#### Settings

The **Settings** tab displays a number of options that can be configured based on the Service Provider in use. These settings can be changed by clicking the fields next to the setting names. Settings marked with an asterisk must be configured.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ia8efd28d3c398145.png)

Some required fields (such as License Key) will open a **Credentials** window. After entering a display name for the credentials, you must provide a **Vault Type,**which will allow one of two options:

- **Local Vault** provides a local encrypted location within the Connect database where service credentials can be locally managed.
- **Azure Key Vault** allows the user to obtain credentials stored in an Azure Key Vault.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i8c59aa018111246f.png)

After choosing a vault type, you must supply values for the **Vault Configuration**.

For **Local Vault**:

- Input the value for your local vault key.

For **Azure Key Vault**:

- **Vault URL**: Specify the Azure Key Vault URL.
- **Tenant ID**: Specify the tenant ID under which your application resides. Retrieve it by hovering the mouse in the top-right corner of the Azure portal.
- **App Registration ID**: (Client ID) : The application ID that's assigned to your app. You can find this information in the portal where you registered your app.
- **App Registration Secret**: (Client Secret): The client secret that you generated for your app in the app registration portal.
- **Secret Name**: Specify the name of secret in Azure Key Vault.

More information about Azure Key Vault can be found here: [Azure Key Vault documentation | Microsoft Learn](https://learn.microsoft.com/en-us/azure/key-vault/?source=recommendations)

More information about OAuth can be found here: [OAuth 2.0 client credentials flow on the Microsoft identity platform - Microsoft identity platform | Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-client-creds-grant-flow#get-a-token)

#### Headers

The **Headers** tab allows you to include a request header to your service configuration to add additional information about the request. Optional key/value pairs that act as a general storage location for information to be included in the request.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ib49a87618983cf68.png)