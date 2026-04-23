# Using the Snowflake Service Provider

The **Snowflake**service provider is a default service provider option included with all versions of Profisee 2025.R1 and beyond, and is included automatically under the list of Service Providers. When you create a Service Configuration, you can select the Snowflake Service provider from the Service Provider dropdown.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i1b2e1735fa810e07.png)

## Add New Configuration

When you create a Service Configuration using this service provider, you must configure it with the following settings:

- **Configuration Name**: The unique name for the configuration
- **Host**: The URL for your Snowflake environment
- **Account**: A unique identifier found within Snowflake under *Snowflake > Home > Account > Account Details > Account Name*
- **Authentication Scheme**: A selection for authentication providers, either Basic or Key Pair (Recommended). Note that Snowflake has stated Basic authentication is slated for deprecation in November 2025.
- **User**: The username for your authentication provider. When provided, you must also select a Name and Vault Type.
- **Name**: The name for this user.
- **Vault Type**: A dropdown selection of Local Vault or Azure Key Vault.
- **Password (Basic Only)**: The password for your Basic authentication provider
- **Private Key****(Key Pair Only, Required)**: The private key for your Key Pair authentication provider
- **Private Key Password****(Key Pair Only, Optional)**: The private key password for your Key Pair authentication provider

For more information about using Key Pair authentication with Snowflake, refer to [this documentation](https://docs.snowflake.com/en/user-guide/key-pair-auth).

Once these settings have been selected, click Continue to continue the Service Provider configuration in the Edit Configuration window.

Once added, the Settings tab for this service provider includes the following settings options:

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-if0fee401a5844be8.png)

### Authentication

The Authentication section allows you to view and edit the Authentication Scheme, User, Password, Private Key, and Private Key Password configured previously. Changing the authentication scheme may require a change in credentials before the configuration can be saved.

### Connection

The Connection section allows you to view the Host URL configured previously, and to view and edit the Account configured previously. From here, you must select a Database before the form can be saved. If no Warehouse is selected, it will use the account's default warehouse.

## Add New Integration Strategy

When adding a new integration strategy using a Snowflake-based Server Configuration, the strategy gains the **Integration Flow** and **Object Name** options.

- **Integration Flow**: Allows the user to Import (From Snowflake into Profisee) or Export (Profisee into Snowflake). If you want to perform both flows, you must create an additional strategy.
- **Object Name**: The Catalog that you wish to import or export. This dropdown is populated based on catalogs created within the Snowflake database specified in the service configuration.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i26a4a6083302f669.png)

When creating an integration strategy for the Snowflake service provider, users with a large number of schema and tables may receive a timeout response in the network tab in dev tools when attempting to request tables for the dropdown to select a table in the integration strategy. You can avoid this by limiting access to only the tables and schema needed.

Once added, the Integration Strategy form includes the following options:

## Run Options

Note that when selecting the Run Options for a Strategy using the Snowflake Service Provider that has an Import integration flow, execution is limited to On-Demand asynchronous execution and Scheduled execution.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibb1091a239f051bd.png)

When selecting the Run Options for a Strategy with an Export integration flow, continuous execution options are available, such as when records are added, updated, or deleted.

When choosing to execute continuously on record delete, you can choose whether to flag the record in the external system for deletion or to delete the record in the external system.

An optional record filter can be applied to each continuous option to limit the number of records to be processed for each of the continuous options.

Execution can also be scheduled. You can enter one or more named scheduled as well as an optional record filter.

### Schedules

Users can add one or more named schedules. A unique name for each schedule is provided by default, but this value can be updated if needed. A new schedule must be added as a [Cron expression](https://cronevery.day/). ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i7d6ddb2b8ac983ba.png)