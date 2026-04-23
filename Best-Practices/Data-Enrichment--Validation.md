# Data Enrichment & Validation

# Best Practices for Data Enrichment & Validation

This guide describes the ways in which you can enhance and validate your master data using the features of the Profisee Platform.  MDM administrators can use it to understand the purpose and compatibility of the different features.

### Data Enrichment & Verification

In MDM programs data enrichment and validation is often needed because the raw data in an organization’s databases is often incomplete, inaccurate, or not useful for meaningful analysis or decision-making. Enrichment adds missing context, improves quality and consistency, and turns data into something actionable.

Profisee supports any data validation and enrichment integrations that you choose to implement, assuming that the inputs and outputs are consistent with the data types available in Profisee.

One type of enrichment that we frequently see in MDM is address verification and standardization for locations, mailing addresses, phone numbers, e-mail addresses. Another common type of data enrichment is for business information like company names, official addresses, industry information, and ownership or organizational structures.

### Custom Data Enrichment & Validation Processes

Integrator allows for development of custom Connectors, but they cannot be deployed into a SaaS environment. Instead, customers should use Connect to implement their custom data integrations with modern REST-based providers. The Connect feature supports custom ‘service providers’ to work with your data enrichment services but Profisee also includes native and supported features for two key types of validation and enrichment.

### Address Verification Services

Profisee FastApp Studio has a built-in Address Verification (AV) feature which natively supports services from Google Maps, Melissa Data v2, and Loqate. You must procure a license/API key from those service providers to make requests with their services. API keys can be embedded in Profisee licenses or provided in FastApp Studio when building your AV strategies.  AV strategies are limited to the service providers and to the attributes provided by the underlying service. The full list of inputs and outputs that you can map is visible in the dialog where you configure the strategies.

AV strategies allow you to configure the service and specify input and output mappings.  You can execute AV requests on demand, or on a schedule, or based on data change events using Real-Time Event Processing.

It’s important to understand that any AV strategies configured to use Melissa Data’s API v2 are considered a legacy feature for existing customers only.  New customers are recommended to use the Connect feature with Melissa Data’s Personator service.

Connect supports strategy processing on demand, on a schedule, or based on data changes. Connect also enables customers to implement custom data integrations with modern REST-based providers.

### Business Information Services

Many Profisee customers rely on information managed by external data providers. The most common one we see is Dun & Bradstreet (D&B).  An organization’s D U N S Number, a unique nine digit identifier, is one of D&B’s most widely used tools. Companies use it to verify legal business entities, link businesses to corporate family trees, standardize vendor records, and validate global partners in supply chains. The D U N S system uniquely identifies businesses worldwide and supports creditworthiness tracking.  Companies use D&B data to make smarter decisions about risk, credit, compliance, sales, marketing, and supplier management.  
Profisee has two features that allow for integration with D&B services.

Profisee Integrator includes a D&B Connector which supports a limited set of data from their Direct+ service. The drawbacks to using this are:  
- Tied to D&B Direct+  
- Installation of Integrator client software and the connector is required,  
- Limited service flavors and attributes (Identity Resolution, Corporate Linkage, Company Profile).  
- Customization is not possible by customers.  
- This is considered a legacy feature, for existing customers only.

New customers should use the Connect feature with D&B’s ‘Data Blocks’ service.  The Connect service providers offer a larger set of data and can be extended to include other values available from the underlying service.  Data Blocks are D&B’s API-based enrichment services that Profisee consumes through a native Connect connector, replacing legacy Integrator-based D&B integrations with a modern, no-code, REST-driven model.

### Best Practices

1. Avoid overwriting input attribute values with output values from the external service. Instead, create dedicated attributes for result values.  Users typically prefer to see the original values alongside the enriched ones.  
2. Some service providers return quality metadata indicators which can be useful in your downstream processes. Capture any available quality or descriptive data if it is included in the response. For example, the Coding Accuracy Support System (CASS) is a USPS certification that confirms an address verification service can accurately standardize and validate U.S. mailing addresses for reliable delivery.    
3. Data and standards can change over time. Decide how often your data needs to be verified or enriched.  For example, some customers choose to verify mailing addresses annually, even if the values have not changed.  
4. People and businesses move, and you should plan your integrations for handling that scenario. Profisee supports National Change of Address (NCOA) processing through certified third party data quality providers (such as Melissa) that are licensed USPS NCOA partners. Through these integrations, Profisee enables organizations to identify and apply address changes submitted to the USPS by individuals and businesses who have moved.