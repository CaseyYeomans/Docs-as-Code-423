# Using the Global Service Providers

## Overview

The Melissa Global Data Quality Service Provider is a default integration component included with Profisee 2025.R1 and later versions. This service provider enables real-time data validation and enrichment by connecting Profisee to Melissa's Global Name, Address, Email, and Phone verification services. The connector follows a REST enrichment pattern where data is sent to Melissa for cleansing and the enhanced results are returned to Profisee.

## Key Features

* Built-in service provider (no additional installation required)
* API Key authentication
* Real-time data validation and enrichment
* Four specialized endpoints: Global Address, Global Name, Global Email, Global Phone
* Flexible execution options (on-demand, scheduled, continuous)
* Separate request and response field mapping
* Integration with Melissa's global data quality services

### Available Service Providers

The Melissa integration includes four distinct service providers:

* **Global Address Service Provider** - Address validation and standardization
* **Global Name Service Provider** - Name parsing and standardization
* **Global Email Service Provider** - Email address validation and verification
* **Global Phone Service Provider** - Phone number validation and formatting

Each service provider must be configured separately based on your data quality requirements.

### Prerequisites

Before configuring any Melissa Service Provider, ensure you have:

* Valid Melissa Global API license and credentials
* API key for the specific service(s) you want to use
* Network connectivity to Melissa's cloud services
* Understanding of your data quality requirements
* Regional licensing appropriate for your data processing needs

## Configuration Setup

### Creating a New Service Configuration

1. Navigate to Service Configurations in Profisee
2. Select "Add New Configuration"
3. Choose the appropriate Melissa service provider from the dropdown:

* Global Address Service Provider
* Global Name Service Provider
* Global Email Service Provider
* Global Phone Service Provider

### Required Configuration Parameters

|  |  |  |  |
| --- | --- | --- | --- |
| **Parameter** | **Description** | **Required** | **Notes** |
| Configuration Name | Unique identifier for the configuration | Yes | Must be unique across all configurations |
| Service Provider | Melissa service type | Yes | Select appropriate global service provider |
| Service | Service endpoint specification | Yes | Autopopulated based on provider selection |
| Operation | Processing operation type | Yes | Real Time or Batch options available |

### Service Configuration Options

* **Service**: /GlobalAddress/doGlobalAddress (auto-populated)
* **Operation**: Select from the available options:
  + **Real-Time Global Address Verify:** Individual record processing
  + **Batch Global Address Verify:** Bulk record processing

## Authentication Configuration

### API Key Setup

1. Navigate to the Settings tab in your configuration.
2. Select **Click to set Credentials** for the API Key field.
3. Configure the options in the Credentials dialog:
   * **Name**: Enter descriptive name (e.g., "Melissa API Key")
   * **Vault Type**: Choose Local Vault or Azure Key Vault
   * **Value**: Enter your Melissa API key
4. In the **Credentials** dialogue:
   * **Name**: Enter descriptive name (e.g., "Melissa API Key")
   * **Vault Type**: Choose Local Vault or Azure Key Vault
   * **Value**: Enter your Melissa API key

## Credential Storage Options

### Local Vault

The local vault allows you to store your API key directly within Profisee, which is suitable for development and testing environments.

### Azure Key Vault

For Azure Key vault, input settings for the following options:

* **Vault URL**: Your Azure Key Vault endpoint
* **Tenant ID**: Azure Active Directory tenant ID
* **App Registration ID**: Azure app registration ID
* **App Registration Secret**: Azure app secret
* **Secret Name**: Name of the API key secret in the vault

## Service-Specific Configuration

Each Melissa service provider handles different data types:

**Global Address Service Provider**

* Validates and standardizes postal addresses worldwide
* Returns standardized address components
* Provides delivery point validation
* Includes geocoding information where available

**Global Name Service Provider**

* Parses full names into components (first, middle, last, prefix, suffix)
* Standardizes name formatting
* Handles international name conventions
* Provides gender determination where applicable

**Global Email Service Provider**

* Validates email address syntax and format
* Checks domain validity and mail server accessibility
* Provides deliverability assessment
* Identifies disposable email addresses

**Global Phone Service Provider**

* Validates phone number format and structure
* Standardizes international phone number formatting
* Provides carrier and line type information
* Determines geographic location information

## Integration Strategy Configuration

### Creating Integration Strategies

When creating an integration strategy with a Melissa service configuration:

1. Navigate to your entity and select "Add New Integration Strategy"
2. Complete the strategy fields:
   * **Strategy Name**: Descriptive name for the integration
   * **Entity**: Source Profisee entity containing data to validate
   * **Service Configuration**: Your configured Melissa service provider
   * **Integration Flow**: Select "Export" (data validation service)
   * **Object Name**: Target endpoint for data processing

### Field Mapping Configuration

The integration strategy includes two mapping tabs:

**Request Mapping Tab**

* Map Profisee entity attributes to Melissa service input parameters
* Configure which fields to send for validation/enrichment
* Set up data transformation expressions if needed

**Response Mapping Tab**

* Map Melissa service output fields back to Profisee entity attributes
* Configure how validated/enriched data is stored
* Handle confidence scores and result codes

## Execution Options

Export Strategies (Profisee → Melissa → Profisee)

### Supported Execution Types

**Continuous Execution**

* Record Addition: Triggered when records are added to Profisee
* Record Updates: Triggered when records are modified in Profisee
* Real-time validation: Immediate data quality processing

**Scheduled Execution**

* Cron-based scheduling: Flexible timing configuration
* Batch processing: Process multiple records efficiently
* Record filtering: Apply criteria to limit processing scope

**On-Demand Execution**

* Manual execution for testing and ad-hoc processing
* Configurable record limits
* Real-time status monitoring

### Record Filtering

Optional record filters can be applied to:

* Process only records meeting specific criteria
* Avoid reprocessing already validated records
* Apply business logic constraints
* Manage API usage and costs effectively

## Schedule Management

### Cron Expression Configuration

Schedules use standard cron expressions with the following format:

\*  \*  \*  \*  \*  \*

│ │ │ │ │ │

│ │ │ │ │ └── Day of week (0-7, Sunday = 0 or 7)

│ │ │ │ └──── Month (1-12)

│ │ │ └────── Day of month (1-31)

│ │ └──────── Hour (0-23)

│ └────────── Minute (0-59)

└──────────── Second (0-59)

### Schedule Management Features

* **Multiple Schedules**: Add multiple named schedules per strategy
* **Batch Optimization**: Schedule bulk processing during off-peak hours
* **API Usage Management**: Distribute processing to manage rate limits

---




# Melissa Data - All Services

[Personator ContactVerify](#Personator-ContactVerify)[Global Address](#Global-Address)[Global Email](#Global-Email)[Global Name](#Global-Name)[Global Phone](#Global-Phone)

## Personator ContactVerify

| Category | Name | Description | Direction | Data Type |
| --- | --- | --- | --- | --- |
| Address | AddressDeliveryInstallation (Canada Only) | Returns the parsed delivery installation for the address entered in the AddressLine field. | Output | string |
| Address | AddressExtras | Any extra information that does not fit in the AddressLine fields. | Output | string |
| Address | AddressHouseNumber | Returns the parsed house number for the address entered in the AddressLine field. | Output | string |
| Address | AddressKey | Returns a unique identifier for an address. This key can be used with other current and future Melissa services. | Output | string |
| Address | AddressLine1 | Street address. If including a suite, you can add it to the end of AddressLine1 field or enter it into the AddressLine2 field. | Input/Output | string |
| Address | AddressLine2 | Street address. Can be a continuation of AddressLine1 (ex: suite) or another address. | Input/Output | string |
| Address | AddressLockBox (Canada Only) | Returns the parsed lock box number for the address entered in the AddressLine field. | Output | string |
| Address | AddressPostDirection | Returns the parsed post-direction for the address entered in the AddressLine field. | Output | string |
| Address | AddressPreDirection | Returns the parsed pre-direction for the address entered in the AddressLine field. | Output | string |
| Address | AddressPrivateMailboxName | Returns the parsed private mailbox name for the address entered in the AddressLine field. | Output | string |
| Address | AddressPrivateMailboxRange | Returns the parsed private mailbox range for the address entered in the AddressLine field. | Output | string |
| Address | AddressRouteService (Canada Only) | Returns the parsed route service number for the address entered in the AddressLine field. | Output | string |
| Address | AddressStreetName | Returns the parsed street name for the address entered in the AddressLine field. | Output | string |
| Address | AddressStreetSuffix | Returns the parsed street suffix for the address entered in the AddressLine field. | Output | string |
| Address | AddressSuiteName | Returns the parsed suite name for the address entered in the AddressLine field. | Output | string |
| Address | AddressSuiteNumber | Returns the parsed suite number for the address entered in the AddressLine field. | Output | string |
| Address | AddressTypeCode | Returns a code for the address type in the AddressLine field. Please see the appendix for the list of possible codes. | Output | string |
| Address | CarrierRoute | Returns a 4-character code defining the carrier route for this record. | Output | string |
| Address | DeliveryIndicator | Returns an indicator of whether an address is a business address or residential address. | Output | string |
| Address | DeliveryPointCheckDigit | Returns a string value containing the 1-digit delivery point check digit. | Output | string |
| Address | DeliveryPointCode | Returns a string value containing the 2-digit delivery point code. | Output | string |
| Address | DistanceAddressToIP | This is the distance in miles between the latitude and longitude of the physical location of the IP Address and the latitude and longitude of the input Address. | Output | string |
| Address | EmailAddress | Email address. | Input/Output | string |
| Address | IPAddress | IP Address. | Input/Output | string |
| Address | MailboxName | Returns the parsed mailbox name for the email entered in the Email field. | Output | string |
| Address | MelissaAddressKey | Melissa Address Key - A proprietary unique key identifier for an address. | Input/Output | string |
| Address | MelissaAddressKeyBase | Returns a unique key associated with a building containing multiple suites/apartments. | Output | string |
| Address | PrivateMailBox | Returns the private mail box number for the address in the AddressLine field, if any. | Output | string |
| Address | Suite | Returns the suite for the address in the AddressLine field, if any. | Output | string |
| Address | UrbanizationName | Returns the urbanization name for the address entered in the AddressLine field. Usually only used if the address is in Puerto Rico. | Output | string |
| Demographic/Census | CBSACode | Census Bureau's Core Based Statistical Area (CBSA). Returns the 5-digit code for the CBSA associated with the requested record. | Output | string |
| Demographic/Census | CBSADivisionCode | Returns the code for a division associated with the requested record, if any. | Output | string |
| Demographic/Census | CBSADivisionLevel | Returns whether the CBSA division, if any, is metropolitan or micropolitan. | Output | string |
| Demographic/Census | CBSADivisionTitle | Returns the title for the CBSA division, if any. | Output | string |
| Demographic/Census | CBSALevel | Returns whether the CBSA is metropolitan or micropolitan. | Output | string |
| Demographic/Census | CBSATitle | Returns the title for the CBSA. | Output | string |
| Demographic/Census | CensusBlock | Returns a 4-digit string containing the census block number associated with the requested record. | Output | string |
| Demographic/Census | CensusKey | Returns a 16 digit string assigned by the US Census Bureau. | Output | string |
| Demographic/Census | CensusTract | Returns a 4-to 6-digit string containing the census tract number associated with the requested record. | Output | string |
| Demographic/Census | CongressionalDistrict | Returns the 2-digit congressional district that the requested record belongs to. | Output | string |
| Demographic/Census | CountyFIPS | Returns the FIPS code for the county in the County field. | Output | string |
| Demographic/Census | CountyName | Returns the county name. | Output | string |
| Demographic/Census | CountySubdivisionCode | Returns a 5 digit string representing the County Subdivision Code for the requested record. | Output | string |
| Demographic/Census | CountySubdivisionName | Returns the County Subdivision Name for the requested record. | Output | string |
| Demographic/Census | ElementarySchoolDistrictCode | Returns a 5 digit string representing the Elementary School District Code for the requested record. | Output | string |
| Demographic/Census | ElementarySchoolDistrictName | Returns the Elementary School District Name for the requested record. | Output | string |
| Demographic/Census | PlaceCode | When ZIP codes overlap, the City field will always return the city that covers most of the ZIP area. | Output | string |
| Demographic/Census | PlaceName | When ZIP codes overlap, the City field will always return the city that covers most of the ZIP area. | Output | string |
| Demographic/Census | SecondarySchoolDistrictCode | Returns a 5 digit string representing the Secondary School District Code for the requested record. | Output | string |
| Demographic/Census | SecondarySchoolDistrictName | Returns the Secondary School District Name for the requested record. | Output | string |
| Demographic/Census | State | State. Accepts either two-character abbreviation or full state name. | Input/Output | string |
| Demographic/Census | StateDistrictLower | Returns a 3 digit string representing the Lower State District Code for the requested record. | Output | string |
| Demographic/Census | StateDistrictUpper | Returns a 3 digit string representing the Upper State District Code for the requested record. | Output | string |
| Demographic/Census | StateName | Returns the full name of the state entered in the State field. | Output | string |
| Demographic/Census | UnifiedSchoolDistrictCode | Returns a 5 digit string representing the Unified School District Code for the requested record. | Output | string |
| Demographic/Census | UnifiedSchoolDistrictName | Returns the Secondary Unified District Name for the requested record. | Output | string |
| Email | TopLevelDomain | Returns the parsed top-level domain name for the email entered in the Email field. | Output | string |
| Geographic | City | City. | Input/Output | string |
| Geographic | CityAbbreviation | Returns an abbreviation for the city entered in the City field, if any. | Output | string |
| Geographic | Country | Country. | Input | string |
| Geographic | CountryCode | Returns the country code for the country in the Country field. | Output | string |
| Geographic | Latitude | Returns the geocoded latitude for the address entered in the AddressLine field. | Output | string |
| Geographic | Longitude | Returns the geocoded longitude for the address entered in the AddressLine field. | Output | string |
| Geographic | PostalCode | Postal Code or ZIP Code. | Input/Output | string |
| Geographic | UTC | Returns the time zone of the requested record. All Melissa products express time zones in UTC (Coordinated Universal Time). | Output | string |
| Household/Lifestyle | ChildrenAgeRange | Returns the age range of children present in the household. | Output | string |
| Household/Lifestyle | CreditCardUser | Returns whether the user has a credit card or not. | Output | string |
| Household/Lifestyle | HouseholdIncome | Returns the range of the household's income. | Output | string |
| Household/Lifestyle | HouseholdSize | Returns the number of occupants in the household. | Output | string |
| Household/Lifestyle | LengthOfResidence | Returns the range of the individual's length of residency in their current address. | Output | string |
| Household/Lifestyle | MoveDate | Returns the date associated with the move address. | Output | string |
| Household/Lifestyle | OwnRent | Returns the individual's status as owner or renter of the property. | Output | string |
| Household/Lifestyle | PresenceOfChildren | Returns the presence of children in the household. | Output | string |
| Household/Lifestyle | PresenceOfSenior | Returns the presence of senior/s in the household. | Output | string |
| IP Address | IPCity | The city where the IP address is located. | Output | string |
| IP Address | IPConnectionSpeed | The connection speed associated with this IP address. | Output | string |
| IP Address | IPConnectionType | The type of connection used by this IP address. | Output | string |
| IP Address | IPContinent | The continent where the IP address is located. | Output | string |
| IP Address | IPCountryAbbreviation | The ISO 3166-1 alpha-2 country code of the country where the IP address is located. | Output | string |
| IP Address | IPLatitude | The latitude for the IP address. This usually points to the IP Address's postal code. | Output | string |
| IP Address | IPLongitude | The longitude for the IP address. This usually points to the IP Address's postal code. | Output | string |
| IP Address | IPPostalCode | The postal code where the IP Address is located. | Output | string |
| IP Address | IPProxyDescription | Additional Details for the Proxy Type returned. | Output | string |
| IP Address | IPProxyType | The type of proxy for an IP Address. | Output | string |
| IP Address | IPRegion | The region where the IP address is located. | Output | string |
| IP Address< |