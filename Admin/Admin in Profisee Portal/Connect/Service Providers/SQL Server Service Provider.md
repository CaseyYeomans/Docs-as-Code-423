# Using the SQL Server Service Provider

The **SQL Server** service provider is a default service provider option included with all versions of Profisee 2025.R0 and beyond, and is included automatically under the list of Service Providers. When you create a Service Configuration, you can select the SQL Server provider from the Service Provider dropdown.

## Add New Configuration

When you create a Service Configuration using this service provider, you must configure it with the following settings:

- **Configuration Name**: The unique name for the configuration.
- **Server Name**: The fully qualified domain name of a SQL Server that has been [configured for use with Connect](https://support.profisee.com/wikis/profiseeplatform/sql_server_deployment_overview).
- **Port (Optional)**: The port that has been configured for the SQL Server database. By default, this is port 1433.
- For SaaS users, the provided default port 1433 is the required port.
- **Encrypt Communications (Optional)**: Enable to encrypt communications.
- **Trust Server Certificate (Optional)**: Enable to trust the server certificate.
- **Authentication Scheme**: Choose between SQL Logon or Entra Service Principal. This determines the Username, Password, and Tenant ID used below.
- **Username**: The username credentials for the associated authenticator.
- **Password**: The password credentials for the associated authenticator.
- **Tenant ID**: The unique identifier assigned to your Azure AD tenant. This is used to authenticate and interact with your Azure resources and services. (Only required for Entra Service Principal).

Once these settings have been selected, click Continue to continue the Service Provider configuration in the Edit Configuration window.

##

Once added, the Settings tab for this service provider includes the following settings options:

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibfbed1ad6b63d905.png)

### Authentication

The Authentication section allows you to view and edit the Authentication Scheme, Username, Password, and Tenant ID configured previously. Changing the authentication scheme may require a change in credentials before the configuration can be saved.

### Connection

The Connection section allows you to view the Server Name and Port configured previously and select the Database. The Database allows you to select a SQL Server Database from the connected SQL Server to use.

### Communication

The Communication section allows you to edit the Encrypt Communications and Trust Server Certificate settings configured previously. It also allows you to configure the number of seconds for Connection Timeout (60 seconds by default) and Command Timeout (120 seconds by default).

## Add New Integration Strategy

When adding a new integration strategy using a SQL-based Server Configuration, the strategy gains the **Integration Flow** and **Object Name** options.

- **Integration Flow**: Allows the user to Import (From SQL into Profisee) or Export (Profisee into SQL). If you want to perform both flows, you must create an additional strategy.
- **Object Name**: The tables/views that you wish to import or export. This dropdown is populated based on tables/views created within the SQL Server database specified in the service configuration. You cannot export to a view.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i355a3d89496d6ccf.png)

Once added, the Integration Strategy form includes the following options:![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ief9988b1903a8df1.png)

### Provider Details

The Provider Details section contains the Strategy Name, Entity, Provider Type, Configuration, and Integration Flow previously configured. Except for Strategy Name, these settings are read-only.

### Object

The Object section provides read-only information on the object, namely whether the Source Type is a Table or View, and the name for that object.

## Run Options

Note that when selecting the Run Options for a Strategy using the SQL Server Service Provider that has an Import integration flow, execution is limited to On-Demand asynchronous execution and Scheduled execution.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3d7cd1c3814a613d.png)

When selecting the Run Options for a Strategy with an Export integration flow, continuous execution options are available, such as when records are added, updated, or deleted.

When choosing to execute continuously on record delete, you can choose whether to flag the record in the external system for deletion or to delete the record in the external system.

An optional record filter can be applied to each continuous option to limit the number of records to be processed for each of the continuous options.

Execution can also be scheduled. You can enter one or more named scheduled as well as an optional record filter.

### Schedules

Users can add one or more named schedules. A unique name for each schedule is provided by default, but this value can be updated if needed. A new schedule must be added as a [Cron expression](https://cronevery.day/).