# Using the Databricks Service Provider

The **Databricks**service provider is a default service provider option included with all versions of Profisee 2025.R1 and beyond, and is included automatically under the list of Service Providers. When you create a Service Configuration, you can select the Databricks Service provider from the Service Provider dropdown.

## Add New Configuration

When you create a Service Configuration using this service provider, you must configure it with the following settings:

- **Configuration Name**: The unique name for the configuration.
- **Databricks URL:** The URL of your existing Databricks environment.
- **Warehouse ID**: A unique identifier found within your Databricks environment. This can be located within *Databricks* > *SQL* > *SQL Warehouses* > *Overview*.
- **Authentication Scheme**: A selection for authentication providers, either ApiKey or OAuth2.
- **API Key**: Authentication credentials, needed only for the ApiKey authentication scheme. If selected, you must determine a Name and Vault type.
- **Name**: The given name for your API Key
- **Vault Type**: Local Vault or Azure Key Vault
- **Client ID**: Your ClientID for your OAuth2 credentials.
- **Client Secret**: Your Client Secret for your OAuth2 credentials.

In order to send and receive data from Databricks, the Service Principal (OAuth) or Personal Access Token (API Key) associated with Profisee must have the following permissions:

- MODIFY
- BROWSE
- EXECUTE
- READ VOLUME
- SELECT
- USE CATALOG
- USE SCHEMA

Once these settings have been selected, click Continue to continue the Service Provider configuration in the Edit Configuration window.

Once added, the Settings tab for this service provider includes the following settings options:

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibfbed1ad6b63d905.png)

### Authentication

The Authentication section allows you to view and edit the Authentication Scheme, API Key, Username, Client Id and Client Secret configured previously. Changing the authentication scheme may require a change in credentials before the configuration can be saved.

### Connection

The Connection section allows you to view the Databricks URL Name and Warehouse ID configured previously, and to select the Catalog from a dropdown populated by your Databricks environment.

## Add New Integration Strategy

When adding a new integration strategy using a Databricks-based Server Configuration, the strategy gains the **Integration Flow** and **Object Name** options.

- **Integration Flow**: Allows the user to Import (From Databricks into Profisee) or Export (Profisee into Databricks). If you want to perform both flows, you must create an additional strategy.
- **Object Name**: The Catalog that you wish to import or export. This dropdown is populated based on catalogs created within the Databricks database specified in the service configuration.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i355a3d89496d6ccf.png)

Once added, the Integration Strategy form includes the following options:![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ief9988b1903a8df1.png)

## Run Options

Note that when selecting the Run Options for a Strategy using the Databricks Service Provider that has an Import integration flow, execution is limited to On-Demand asynchronous execution and Scheduled execution.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3d7cd1c3814a613d.png)

When selecting the Run Options for a Strategy with an Export integration flow, continuous execution options are available, such as when records are added, updated, or deleted.

When choosing to execute continuously on record delete, you can choose whether to flag the record in the external system for deletion or to delete the record in the external system.

An optional record filter can be applied to each continuous option to limit the number of records to be processed for each of the continuous options.

Execution can also be scheduled. You can enter one or more named scheduled as well as an optional record filter.

### Schedules

Users can add one or more named schedules. A unique name for each schedule is provided by default, but this value can be updated if needed. A new schedule must be added as a [Cron expression](https://cronevery.day/).