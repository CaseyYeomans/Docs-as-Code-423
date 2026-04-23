# Setting Up Authentication using OAuth 2.0 Resource Owner Password Credentials Flow

In order to connect to a SQL Database in Azure, Connect requires an App Registration to be created in Microsoft Entra that represents the Profisee instance. To create an Azure App Registration to connect to an Azure SQL Database instance:

## 1. Navigate to Azure Active Directory

1. Go to the Azure portal and select **Azure Active Directory** from the left-hand menu.

## 2. Create a New App Registration

1. Click **App registrations** and then **New registration**.
2. Enter a name for the app (e.g., "SQL Database Connector").
3. Select the supported account types (e.g., "Accounts in this organizational directory only").
4. Click **Register**.

## 3. Configure API Permissions

After creating the app registration, navigate to the app's **API permissions** section.

NOTE: For SQL Server access, access permissions are assigned by executing the SQL outlined in the step labeled *Assign Permissions to the App* below.

## 4. Generate a Client Secret

1. Go to the **Certificates & secrets** section.
2. Click on **New client secret** and provide a description and expiry period.
3. Click **Add** and note down the client secret value because you will only be able to see this once. We recommend recording this value in a supported Password Vault (AKV, 1Passord, etc). This will be used for authentication.

## 5. Set Up a Connection String

1. Use the client ID, tenant ID, and client secret to configure your connection string for the Azure SQL Database instance. The connection string format will be similar to:

```
Server=tcp:<your_server>.database.windows.net,1433;Database=<your_database>;Authentication=Active Directory Service Principal;UID=<client_id>;PWD=<client_secret>
```

## 6. Assign Permissions to the App

1. Navigate to your Azure SQL Database instance.
2. Go to **Set server firewall** and ensure your IP address is allowed.
3. Open SQL Server Management Studio (SSMS) or Azure Data Studio.
4. Connect to the database using an admin account and run the following SQL command to assign permissions to the app:

```
CREATE USER [<app_name>] FROM EXTERNAL PROVIDER;

EXEC sp_addrolemember 'db_datareader', '<app_name>';

EXEC sp_addrolemember 'db_datawriter', '<app_name>';
```

## Note

To query an Azure SQL Server's master database and determine which databases your service principal has access to, you can use the following T-SQL query:

```
SELECT name
FROM sys.databases
WHERE HAS_DBACCESS(name) = 1;
```

This query will list all databases on the server where your service principal has access.

## Finish

Once these steps are completed, you have successfully created an Azure App Registration that can connect to an Azure SQL Database instance. You may now continue to the next step, [Create a Fabric Warehouse](https://support.profisee.com/wikis/profiseeplatform/create_a_fabric_warehouse).