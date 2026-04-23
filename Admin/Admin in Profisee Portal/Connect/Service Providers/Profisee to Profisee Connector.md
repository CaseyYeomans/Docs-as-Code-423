# Using the Profisee to Profisee Connector

The Profisee to Profisee Connector enables data migration between two Profisee instances or between entities within the same instance. This connector operates in export mode only. To create bidirectional data flow, configure separate connectors in reverse direction.

## Prerequisites

The following conditions must be fulfilled to use this Service Provider:

- Super Admin role required to access Connect
- XAPI authentication keys for target Profisee instance
- Access to credential vault (Local Vault or Azure Key Vault)

## Configuration Setup

To create a new configuration:

1. Click Add New Configuration
2. Complete the required fields:
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-idb58f7cb417033fe.png)

- **Configuration Name**: Enter a descriptive name (e.g., "Profisee to Profisee").
- **Service Provider**: Select "Profisee Service Provider" from dropdown.
- **Profisee URL**: Enter the URL of the target Profisee instance where data will be exported.
- **Client ID**: Click "Click to set Credentials" to open the credential vault. The Credentials dialog opens.
- **Name**: Enter a name for your credential (e.g., "Client ID")
- **Vault Type**: Choose your vault type:
- **Local Vault**: For credentials stored locally
- **Value**: Enter your XAPI authentication key. This can be found in your target environment. Navigate to FastApp Studio > Accounts and Teams. Enable Unattended Authentication for the initiating user and copy the API key provided.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i6d5b4672ef29dff6.png)
- **Azure Key Vault**: For credentials stored in Azure.
- **Vault URL**: Azure Key Vault URL
- **Tenant ID**: Azure tenant identifier
- **App Registration ID**: Azure app registration ID
- **App Registration Secret**: Azure app secret
- **Secret Name**: Name of the secret in the vault

3. Click **Continue** to save the input credentials.

## Configure Provider Details

Navigate to the **Overview** tab and configure the following options:

- Configuration Name: Displays your entered name
- Service Provider: Shows "Profisee Service Provider"
- Provider Type: Shows "Database"
- Database Type: Shows "Profisee"

## Authentication and Connection Settings

1. Navigate to the **Settings** tab and configure the following options:

- **Authentication**:
- **Client ID**: Displays the name provided for your configured credential
- **Connection**:
- **Profisee URL**: Shows your target instance URL
- **Communication**:
- **Command Timeout (sec)**: Set timeout value (default: 120 seconds)
- **Ignore Constraint Rules**: Check to bypass constraint validation
- **Auto Add All DBAs**: Check to automatically add domain based attributes

2. Click **Save** or **Save** **and Close** to complete configuration.

## Creating Export Strategies

1. Click the **+** to create a new strategy.
2. Complete the **Add New Integration Strategy** dialog:![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i9017b6274b9c17c0.png)

- **Strategy Name** - A user-defined name to identify this integration strategy (shown as "Profisee" in the example)
- **Entity** - The source entity in the current Profisee instance that you want to export data from (shown as "Agency" in the example)
- **Service Configuration** - The previously configured connector that defines the target system connection (shown as "Profisee copy" which would be one of the configurations created in the earlier steps)
- **Integration Flow** - The direction of data movement, set to "Export" since this connector only supports exporting data from the source to the target
- **Object Name** - The target entity or table in the destination system where the data will be imported (shown as "Profisee.Table.AddressVerificationCode" suggesting this is selecting a specific table in the target Profisee instance)

3. Click **Continue** to navigate to the next form.

## Set Up Export Mapping

1. Navigate to **Export Map** tab
2. Use the **Entity Selection** tool to map target entity attributes (left) to source entity attributes (right).

## Configure Field Mapping

For Manual Mapping:

1. Select the target attribute from the left column.
2. Select the corresponding source attribute from the right column.
3. If desired, you can create expressions for complex data manipulation, or use the AI Mapping Assistant to automatically create 1:1 field mappings.

## Configure Run Options

1. Navigate to **Run Options** tab and configure the following options:

- **Execution Settings**
- Run-as user: Select user context for execution
- Maximum records per job: Set batch size limit (default: 1000)
- Trigger Options:
- On-Demand asynchronous execution: Manual execution
- Trigger when records are added: Auto-run on new records
- Trigger when records are updated: Auto-run on record changes
- Trigger when records are deleted: Auto-run on deletions
- Delete records from target: Remove records from target system
- **Filter Configuration**
- Added records filter: Define criteria for new records
- Updated records filter: Define criteria for changed records
- Delete records filter: Define criteria for deletion

## Schedule Execution

1. Navigate to Scheduling tab:

- Enter cron expression for automated execution schedule
- Leave blank for manual/continuous execution