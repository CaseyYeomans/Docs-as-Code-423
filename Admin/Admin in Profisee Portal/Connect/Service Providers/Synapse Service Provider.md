# Using the Synapse Service Provider

The Azure Synapse Analytics Service Provider is a default integration component included with Profisee 2025.R1 and later versions. This service provider enables seamless data integration between Profisee and Azure Synapse Analytics environments, supporting both import and export operations.

**Key Features**

- Built-in service provider (no additional installation required)
- Supports Entra Service Principal and SQL Logon authentication schemes
- Bidirectional data flow (import from/export to Synapse)
- Flexible execution options (on-demand, scheduled, continuous)
- Integration with Azure Synapse SQL pools and databases

## Prerequisites

Before configuring the Azure Synapse Service Provider, ensure you have:

- Access to an Azure Synapse Analytics workspace
- Appropriate authentication credentials (Service Principal or SQL Logon)
- Azure Synapse SQL pool configured and running
- Required permissions for database and table access
- Network connectivity between Profisee and Azure Synapse

## Configuration

### Creating a New Service Configuration

1. Navigate to Service Configurations in Profisee.
2. Select **Add New Configuration**.
3. Choose **Synapse SQL Database Service Provider** from the Service Provider dropdown.

### Required Configuration Parameters

| | | | |
| --- | --- | --- | --- |
| **Parameter** | **Description** | **Required** | **Notes** |
| Configuration Name | Unique identifier for the configuration | Yes | Must be unique across all configurations |
| Server Name | Azure Synapse server endpoint | Yes | Format: mysynapse-ondemand.sql.azuresynapse.net |
| Authentication Scheme | Authentication method | Yes | Options: Entra Service Principal or SQL Logon |
| Username | Authentication username/principal | Yes | Service Principal App ID or SQL username |
| Password | Authentication password/secret | Yes | Service Principal secret or SQL password |
| Tenant ID | Azure Active Directory tenant ID | No | Required for Service Principal authentication |

### Authentication Configuration

Configure authentication by selecting **Click to set Credentials** for Username and Password fields, which opens the **Credentials** popup.

### Credentials Setup

1. **Name:** Enter a descriptive identifier for your credentials
2. **Vault Type**: Select where to store credentials:

- **Local Vault**: Store within Profisee
- **Azure Key Vault:** Store in Azure Key Vault

## Authentication Types

### Entra Service Principal Authentication (Recommended)

1. Set Authentication Scheme to **Entra Service Principal**.
2. Configure Username with Service Principal Application (Client) ID.
3. Configure Password with Service Principal client secret.
4. Enter Tenant ID for your Azure Active Directory.

### SQL Logon Authentication

1. Set Authentication Scheme to **SQL Logon**
2. Configure Username with SQL login username
3. Configure Password with SQL login password
4. Tenant ID not required for SQL authentication

## Service Configuration Settings

### Authentication

The Authentication section allows modification of:

- Authentication scheme (Entra Service Principal <-> SQL Logon)
- Credential information
- Vault configuration

Changing the authentication scheme may require updating credentials before the configuration can be saved.

### Connection

The Connection section displays:

- **Server Name**: Azure Synapse server endpoint (read-only)
- **Database**: Select specific database within your Synapse workspace from dropdown

The database dropdown is dynamically populated based on databases available in the specified Azure Synapse server.

### Communication

Configure connection and security settings:

- Encrypt Communications: Enable SSL/TLS encryption (recommended)
- Trust Server Certificate: Check if using self-signed certificates
- Connection Timeout (sec): Set connection timeout value (default: 60 seconds)
- Command Timeout (sec): Set command execution timeout (default: 120 seconds)

## Integration Strategy Configuration

### Creating an Integration Strategy

When creating an integration strategy with a Synapse service configuration, you must specify:

- Integration Flow
- **Import** Data flows from Synapse to Profisee
- **Export** Data flows from Profisee to Synapse

Each strategy supports only one direction. To enable bidirectional data flow, create separate strategies for import and export.

- Object Configuration
- **Object Name**: Select the database table or view for data operations
- **Selection format**: database.schema.table or database.schema.view
- Execution Options
- **Import strategies** (Synapse to Profisee)
- Execution Type
- **On-Demand Asynchronous**: Manual execution with background processing
- **Scheduled**: Time-based execution using cron expressions

Note that continuous execution is not supported for import operations.

## Export Strategies (Profisee to Synapse)

Supported execution types include:

- Record Addition: Triggered when records are added to Profisee
- Record Updates: Triggered when records are modified in Profisee
- Record Deletion: Triggered when records are deleted in Profisee

Deletion handling options:

- Flag records for deletion in Synapse.
- Physically delete records in Synapse.
- Scheduled Execution:
- Cron-based scheduling: Flexible timing configuration
- Named schedules: Multiple schedules per strategy
- Record filtering: Optional filtering for continuous and scheduled operations

On-Demand Execution

- Manual execution with background processing
- Configurable record limits
- Real-time status monitoring

Record Filtering

Optional record filters can be applied to:

- Limit processing scope for continuous operations
- Reduce data volume for scheduled executions
- Apply business logic constraints

## Schedule Management

**Cron Expression Configuration**
Schedules use standard cron expressions with the following format:

\* \* \* \* \* \*
| | | | | |
| | | | | `-- Day of week (0-7, Sunday = 0 or 7)
| | | | `---- Month (1-12)
| | | `------ Day of month (1-31)
| | `-------- Hour (0-23)
| `---------- Minute (0-59)
`------------ Second (0-59)
**Schedule Management Features**

- **Multiple Schedules**: Add multiple named schedules per strategy
- **Unique Naming**: Default names provided, customizable as needed
- **Schedule Validation**: Automatic validation of cron expressions