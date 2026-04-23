# Using the Global Service Providers

## Overview

The Melissa Global Data Quality Service Provider is a default integration component included with Profisee 2025.R1 and later versions. This service provider enables real-time data validation and enrichment by connecting Profisee to Melissa's Global Name, Address, Email, and Phone verification services. The connector follows a REST enrichment pattern where data is sent to Melissa for cleansing and the enhanced results are returned to Profisee.

## Key Features

- Built-in service provider (no additional installation required)
- API Key authentication
- Real-time data validation and enrichment
- Four specialized endpoints: Global Address, Global Name, Global Email, Global Phone
- Flexible execution options (on-demand, scheduled, continuous)
- Separate request and response field mapping
- Integration with Melissa's global data quality services

### Available Service Providers

The Melissa integration includes four distinct service providers:

- **Global Address Service Provider** - Address validation and standardization
- **Global Name Service Provider** - Name parsing and standardization
- **Global Email Service Provider** - Email address validation and verification
- **Global Phone Service Provider** - Phone number validation and formatting

Each service provider must be configured separately based on your data quality requirements.

### Prerequisites

Before configuring any Melissa Service Provider, ensure you have:

- Valid Melissa Global API license and credentials
- API key for the specific service(s) you want to use
- Network connectivity to Melissa's cloud services
- Understanding of your data quality requirements
- Regional licensing appropriate for your data processing needs

## Configuration Setup

### Creating a New Service Configuration

1. Navigate to Service Configurations in Profisee
2. Select "Add New Configuration"
3. Choose the appropriate Melissa service provider from the dropdown:

- Global Address Service Provider
- Global Name Service Provider
- Global Email Service Provider
- Global Phone Service Provider

### Required Configuration Parameters

| | | | |
| --- | --- | --- | --- |
| **Parameter** | **Description** | **Required** | **Notes** |
| Configuration Name | Unique identifier for the configuration | Yes | Must be unique across all configurations |
| Service Provider | Melissa service type | Yes | Select appropriate global service provider |
| Service | Service endpoint specification | Yes | Autopopulated based on provider selection |
| Operation | Processing operation type | Yes | Real Time or Batch options available |

### Service Configuration Options

- **Service**: /GlobalAddress/doGlobalAddress (auto-populated)
- **Operation**: Select from the available options:
- **Real-Time Global Address Verify:** Individual record processing
- **Batch Global Address Verify:** Bulk record processing

## Authentication Configuration

### API Key Setup

1. Navigate to the Settings tab in your configuration.
2. Select **Click to set Credentials** for the API Key field.
3. Configure the options in the Credentials dialog:
- **Name**: Enter descriptive name (e.g., "Melissa API Key")
- **Vault Type**: Choose Local Vault or Azure Key Vault
- **Value**: Enter your Melissa API key
4. In the **Credentials** dialogue:
- **Name**: Enter descriptive name (e.g., "Melissa API Key")
- **Vault Type**: Choose Local Vault or Azure Key Vault
- **Value**: Enter your Melissa API key

## Credential Storage Options

### Local Vault

The local vault allows you to store your API key directly within Profisee, which is suitable for development and testing environments.

### Azure Key Vault

For Azure Key vault, input settings for the following options:

- **Vault URL**: Your Azure Key Vault endpoint
- **Tenant ID**: Azure Active Directory tenant ID
- **App Registration ID**: Azure app registration ID
- **App Registration Secret**: Azure app secret
- **Secret Name**: Name of the API key secret in the vault

## Service-Specific Configuration

Each Melissa service provider handles different data types:

**Global Address Service Provider**

- Validates and standardizes postal addresses worldwide
- Returns standardized address components
- Provides delivery point validation
- Includes geocoding information where available

**Global Name Service Provider**

- Parses full names into components (first, middle, last, prefix, suffix)
- Standardizes name formatting
- Handles international name conventions
- Provides gender determination where applicable

**Global Email Service Provider**

- Validates email address syntax and format
- Checks domain validity and mail server accessibility
- Provides deliverability assessment
- Identifies disposable email addresses

**Global Phone Service Provider**

- Validates phone number format and structure
- Standardizes international phone number formatting
- Provides carrier and line type information
- Determines geographic location information

## Integration Strategy Configuration

### Creating Integration Strategies

When creating an integration strategy with a Melissa service configuration:

1. Navigate to your entity and select "Add New Integration Strategy"
2. Complete the strategy fields:
- **Strategy Name**: Descriptive name for the integration
- **Entity**: Source Profisee entity containing data to validate
- **Service Configuration**: Your configured Melissa service provider
- **Integration Flow**: Select "Export" (data validation service)
- **Object Name**: Target endpoint for data processing

### Field Mapping Configuration

The integration strategy includes two mapping tabs:

**Request Mapping Tab**

- Map Profisee entity attributes to Melissa service input parameters
- Configure which fields to send for validation/enrichment
- Set up data transformation expressions if needed

**Response Mapping Tab**

- Map Melissa service output fields back to Profisee entity attributes
- Configure how validated/enriched data is stored
- Handle confidence scores and result codes

## Execution Options

Export Strategies (Profisee -> Melissa -> Profisee)

### Supported Execution Types

**Continuous Execution**

- Record Addition: Triggered when records are added to Profisee
- Record Updates: Triggered when records are modified in Profisee
- Real-time validation: Immediate data quality processing

**Scheduled Execution**

- Cron-based scheduling: Flexible timing configuration
- Batch processing: Process multiple records efficiently
- Record filtering: Apply criteria to limit processing scope

**On-Demand Execution**

- Manual execution for testing and ad-hoc processing
- Configurable record limits
- Real-time status monitoring

### Record Filtering

Optional record filters can be applied to:

- Process only records meeting specific criteria
- Avoid reprocessing already validated records
- Apply business logic constraints
- Manage API usage and costs effectively

## Schedule Management

### Cron Expression Configuration

Schedules use standard cron expressions with the following format:

\* \* \* \* \* \*

| | | | | |

| | | | | `-- Day of week (0-7, Sunday = 0 or 7)

| | | | `---- Month (1-12)

| | | `------ Day of month (1-31)

| | `-------- Hour (0-23)

| `---------- Minute (0-59)

`------------ Second (0-59)

### Schedule Management Features

- **Multiple Schedules**: Add multiple named schedules per strategy
- **Batch Optimization**: Schedule bulk processing during off-peak hours
- **API Usage Management**: Distribute processing to manage rate limits