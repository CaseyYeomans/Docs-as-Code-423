# Profisee MDM Components

---

# Profisee MDM Platform Components

## Overview

The Profisee Master Data Management (MDM) platform is a comprehensive, enterprise-grade solution built on a modular architecture that supports multi-domain master data management. The platform consists of numerous integrated components that work together to ingest data from source systems, apply data quality and governance rules, create golden records through matching and survivorship, and distribute trusted master data to downstream consumers.

This document provides a detailed explanation of each component, their interactions, and how data flows through the Profisee platform from source systems to business intelligence and operational systems.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-icd20fbe5cf791cd6.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i8bea5b4d1de3af63.png)

## Architecture Overview

The Profisee platform architecture can be conceptually divided into several functional layers:

* **Data Ingestion Layer**: Receives data from various source systems through initial and ongoing loads
* **Data Processing Layer**: Applies data quality rules, matching algorithms, and governance policies
* **Core Data Layer**: The MDM Hub stores master data entities, attributes, and hierarchies
* **Integration Layer**: Platform API Gateway connects all components and exposes APIs
* **User Interface Layer**: Studio for administrators and FastApps for data stewards
* **Distribution Layer**: Publishes master data to external systems through various channels
* **External Enrichment**: Integration with third-party data quality and enrichment services

## Component Catalog

### A. MDM Hub (Schema/Data)

The MDM Hub is the central repository and heart of the Profisee platform:

* **Master Data Storage**: Stores all master data entities, attributes, and their relationships in a relational database (RDBMS)
* **Multi-Domain Support**: Manages multiple master data domains including Customer, Product, Reference data, and custom domains
* **Entities**: Defines the structure of master data objects (e.g., Customer, Product, Supplier)
* **Attributes**: The individual data elements that make up entities (e.g., Customer Name, Product SKU, Address)
* **Hierarchies**: Organizational structures and relationships between entities (e.g., product categories, location hierarchies, organizational charts)
* **Metadata Management**: Stores configuration, business rules, and metadata about the master data
* **Versioning**: Maintains historical versions of master data records for audit and compliance
* **Cross-References**: Links master data records to their source system identifiers

### B. Platform API Gateway

The Platform API Gateway is the central integration hub that connects all Profisee components:

* **RESTful APIs**: Exposes comprehensive REST APIs for all platform operations
* **Request Routing**: Routes API requests to appropriate backend services
* **Authentication & Authorization**: Validates tokens and enforces security policies
* **Rate Limiting**: Protects backend services from overload
* **API Versioning**: Supports multiple API versions for backward compatibility
* **Request/Response Transformation**: Handles data format conversions and mappings
* **Logging & Monitoring**: Tracks all API calls for auditing and performance monitoring

### C. Data Staging

Data Staging is the entry point for data entering the Profisee platform:

* **Initial Load**: Handles bulk data loads when first implementing Profisee or onboarding new data sources
* **Ongoing Load**: Processes incremental updates from source systems
* **Staging Tables**: Temporary tables where incoming data is held before processing
* **Data Validation**: Performs initial validation checks on incoming data
* **Error Handling**: Identifies and logs records that fail validation
* **Data Transformation**: Applies initial transformations to align with target schema
* **Batch Processing**: Groups records for efficient processing

### D. Ongoing Load

Ongoing Load manages continuous data synchronization from source systems:

* **Incremental Updates**: Processes only changed records rather than full refreshes
* **Change Data Capture**: Detects changes in source systems
* **Scheduled Jobs**: Runs on defined schedules (hourly, daily, real-time)
* **Delta Detection**: Identifies what has changed since the last load
* **Source System Integration**: Connects to multiple heterogeneous source systems

### E. Data Quality Rules

Data Quality Rules enforce standards and validation logic on master data:

* **Validation Rules**: Check data against defined criteria (e.g., email format, phone number patterns)
* **Business Rules**: Enforce business logic and constraints (e.g., customer must have valid address)
* **Completeness Checks**: Ensure required fields are populated
* **Consistency Rules**: Validate data across related attributes (e.g., city matches postal code)
* **Range Validation**: Check numeric and date values fall within acceptable ranges
* **Custom Rules**: Support for complex, organization-specific validation logic
* **Rule Priority**: Execute rules in defined order
* **Error Reporting**: Flag records that fail validation for steward review

### F. Data Quality Strategies

Data Quality Strategies define comprehensive approaches to data quality management:

* **Standardization**: Normalize data to consistent formats (e.g., "Street" vs "St.", "Road" vs "Rd.")
* **Parsing**: Break compound fields into individual components (e.g., full name into first/last)
* **Validation**: Apply multiple validation rules as a coordinated strategy
* **Enrichment**: Enhance data with additional information from external sources
* **Cleansing**: Remove duplicates, correct errors, and fill missing values
* **Address Verification**: Validate and standardize addresses using external services
* **Geocoding**: Add latitude/longitude to address records
* **Strategy Templates**: Pre-built strategies for common data quality scenarios

### G. Matching & Survivorship

Matching & Survivorship creates golden records by identifying and consolidating duplicates:

* **Match Rules**: Define criteria for identifying potential duplicate records
* **Fuzzy Matching**: Use algorithms to find similar but not identical records (e.g., "John Smith" vs "Jon Smith")
* **Match Scoring**: Assign confidence scores to potential matches
* **Auto-Merge Thresholds**: Automatically merge records above a confidence threshold
* **Manual Review Queue**: Send medium-confidence matches to data stewards for review
* **Survivorship Rules**: Determine which values to keep when merging duplicate records
* **Source Trust**: Assign trust scores to source systems (e.g., prefer data from CRM over legacy system)
* **Recency Rules**: Prefer more recently updated values
* **Completeness Rules**: Prefer values from more complete records
* **Golden Record Creation**: Produce the single, authoritative version of each entity

### H. Security

Security component enforces access control and data protection throughout the platform:

* **Authentication**: Verify user identities through Azure AD, OIDC, or other identity providers
* **Role-Based Access Control (RBAC)**: Assign permissions based on user roles
* **Attribute-Level Security**: Control access to specific attributes (e.g., hide SSN from certain users)
* **Entity-Level Security**: Restrict access to entire entities or domains
* **Row-Level Security**: Filter data based on user attributes (e.g., sales reps see only their accounts)
* **Data Masking**: Obfuscate sensitive data for unauthorized users
* **Audit Logging**: Track all data access and changes for compliance
* **Encryption**: Protect data at rest and in transit

### I. Master Data Views

Master Data Views provide optimized access to master data for reporting and analytics:

* **Golden Record Views**: Simplified views showing only the current golden records
* **Flattened Views**: Denormalized views for easier querying and reporting
* **Hierarchical Views**: Expose parent-child and organizational hierarchies
* **Cross-Reference Views**: Show mappings between master data IDs and source system IDs
* **Historical Views**: Access point-in-time versions of master data
* **Quality Metrics Views**: Expose data quality scores and metrics
* **Performance Optimization**: Indexed and materialized for fast query performance
* **BI Tool Integration**: Direct connectivity for Power BI, Tableau, and other BI tools

### J. Real-Time Event Processing

Real-Time Event Processing enables immediate reaction to master data changes:

* **Change Detection**: Monitor master data for changes in real-time
* **Event Publishing**: Publish events when master data is created, updated, or deleted
* **Event Streaming**: Stream events to subscribers via message queues or event hubs
* **Webhook Support**: HTTP callbacks to notify external systems of changes
* **Event Filtering**: Subscribe to specific entity types or change types
* **Guaranteed Delivery**: Ensure events are not lost
* **Event History**: Maintain audit trail of all events

### K. Workflow

Workflow manages business processes around master data stewardship:

* **Approval Workflows**: Route new or changed records through approval chains
* **Task Assignment**: Assign data quality issues to specific stewards
* **Task Queues**: Organize work for data stewards by priority and type
* **Notifications**: Alert users of pending tasks via email or in-app notifications
* **Escalation**: Automatically escalate overdue tasks to managers
* **Workflow Templates**: Pre-built workflows for common scenarios
* **Custom Workflows**: Build organization-specific approval processes
* **SLA Tracking**: Monitor and enforce service level agreements
* **Audit Trail**: Complete history of workflow actions and decisions

### L. Integrator

Integrator connects Profisee with external systems for real-time and batch integration:

* **Real-Time Integration**: Immediate synchronization with external systems like Salesforce and Dynamics 365
* **Bi-Directional Sync**: Support for both reading from and writing to external systems
* **API Connectivity**: REST and SOAP API integrations
* **Database Connectivity**: Direct connections to external databases
* **File-Based Integration**: Import/export via CSV, XML, JSON files
* **Message Queue Integration**: Publish and consume from message queues
* **Transform & Map**: Convert data formats between systems
* **Error Handling**: Retry logic and error notification
* **Scheduling**: Configure batch integration schedules

### M. SDK & APIs

Software Development Kit and APIs enable programmatic access to Profisee:

* **REST API**: Comprehensive RESTful API for all platform operations
* **.NET SDK**: Native SDK for .NET applications
* **Python SDK**: SDK for Python-based integrations
* **Java SDK**: SDK for Java applications
* **PowerShell Module**: Cmdlets for PowerShell scripting and automation
* **Swagger/OpenAPI**: API documentation and testing interface
* **Sample Code**: Example implementations for common scenarios
* **Webhooks**: Subscribe to events via HTTP callbacks

### N. Presentation Views

Presentation Views format master data for optimal display in user interfaces:

* **UI-Optimized Views**: Pre-formatted data for display in web and mobile interfaces
* **Calculated Fields**: Derived attributes computed on-the-fly
* **Formatted Output**: Apply display formatting (e.g., currency symbols, date formats)
* **Localization**: Support multiple languages and locales
* **Aggregations**: Pre-calculated summaries and rollups
* **Search Optimization**: Indexed for fast search and autocomplete

### O. Forms

Forms provide user interfaces for data entry and editing:

* **Dynamic Forms**: Automatically generated based on entity schema
* **Custom Layouts**: Configurable form layouts to match business needs
* **Validation**: Client-side and server-side validation of user input
* **Field-Level Help**: Tooltips and help text for users
* **Conditional Fields**: Show/hide fields based on other field values
* **Lookup Integration**: Searchable dropdowns for related entities
* **Multi-Step Wizards**: Guide users through complex data entry
* **Mobile-Responsive**: Forms adapt to different screen sizes

### P. Portal Applications

Portal Applications are purpose-built user interfaces for specific business scenarios:

* **Customer Portal**: Self-service portal for customers to view and update their information
* **Supplier Portal**: Allow suppliers to maintain their own master data
* **Product Information Management**: Specialized interface for managing product data
* **Data Stewardship Portal**: Optimized interface for data quality tasks
* **White-Label Portals**: Customizable branding for external-facing portals
* **Role-Based Dashboards**: Personalized views based on user role
* **Embedded Analytics**: Charts and metrics within portal interfaces

### Q. Reports

Reports provide insights into master data quality, usage, and trends:

* **Data Quality Reports**: Metrics on completeness, accuracy, and consistency
* **Stewardship Reports**: Track data steward productivity and SLA compliance
* **Match Review Reports**: Summary of matching activities and decisions
* **Audit Reports**: Who changed what and when
* **Custom Reports**: Build organization-specific reports
* **Scheduled Reports**: Automatically generate and distribute reports
* **Export Options**: PDF, Excel, CSV export formats
* **Report Templates**: Pre-built reports for common scenarios

### R. Stewardship

Stewardship provides the interface and workflows for data stewards to manage master data quality:

* **Task Dashboard**: View all pending data quality tasks
* **Match Review**: Review and approve/reject suggested matches
* **Exception Management**: Handle records that failed validation
* **Bulk Operations**: Update multiple records simultaneously
* **Search & Browse**: Find and navigate master data records
* **Data Lineage View**: See the source and history of data values
* **Quality Scoring**: View data quality scores for records
* **Collaboration Tools**: Notes, comments, and task assignment

### S. Studio

Studio is the administrative interface for configuring and managing the Profisee platform:

* **Data Modeling**: Define entities, attributes, and relationships
* **Business Rules Configuration**: Create and manage validation rules
* **Matching Configuration**: Define match rules and survivorship strategies
* **Workflow Design**: Build approval workflows
* **Integration Configuration**: Set up connections to external systems
* **Security Administration**: Manage users, roles, and permissions
* **Form Designer**: Create custom forms and layouts
* **Report Builder**: Design custom reports
* **System Settings**: Configure platform-wide settings
* **Deployment Management**: Migrate configurations between environments

### T. Archiving & Deployment

Archiving & Deployment manages configuration lifecycle and data retention:

* **Configuration Export**: Export entity models, rules, and workflows as packages
* **Configuration Import**: Import packages into other environments
* **Version Control**: Track changes to configurations over time
* **Environment Promotion**: Move configurations from dev to test to production
* **Rollback Capability**: Revert to previous configuration versions
* **Data Archiving**: Move old or inactive records to archive storage
* **Retention Policies**: Define how long data should be retained
* **Backup & Restore**: Backup configurations and data for disaster recovery

### U. Administration

Administration provides tools for ongoing platform management:

* **User Management**: Create and manage user accounts
* **Role Management**: Define and assign roles with specific permissions
* **License Management**: Track and manage user licenses
* **System Monitoring**: View platform health and performance metrics
* **Job Scheduling**: Configure and monitor scheduled jobs
* **Log Management**: Access system logs for troubleshooting
* **Performance Tuning**: Optimize database and application performance
* **Notification Configuration**: Set up email and system notifications
* **Audit Log Access**: Review audit trails for compliance

## External Data Quality and Enrichment Services

Profisee integrates with leading third-party data quality and enrichment services to enhance master data:

### Bing Maps

* **Geocoding**: Convert addresses to latitude/longitude coordinates
* **Reverse Geocoding**: Convert coordinates to addresses
* **Address Validation**: Verify addresses exist and are correctly formatted
* **Distance Calculation**: Calculate distances between locations

### Melissa

* **Address Verification**: Validate and standardize U.S. and international addresses
* **NCOA Processing**: Update addresses using National Change of Address database
* **Email Verification**: Validate email addresses
* **Phone Validation**: Verify and standardize phone numbers
* **Name Parsing**: Parse full names into first, middle, last components

### Loqate

* **Global Address Validation**: Verify addresses in over 240 countries
* **Address Autocomplete**: Real-time address suggestions as users type
* **Email Verification**: Real-time email validation
* **Phone Verification**: Validate phone numbers globally

### Dun & Bradstreet

* **Business Intelligence**: Enrich company records with firmographic data
* **D-U-N-S Number**: Assign unique business identifiers
* **Credit Risk**: Add credit scores and risk assessments
* **Company Hierarchy**: Identify corporate family trees and relationships
* **Industry Classification**: Standardize industry codes (SIC, NAICS)

### Personator Consumer

* **Identity Verification**: Verify consumer identities
* **Demographic Enrichment**: Add age, income, and other demographic data
* **Contact Append**: Add missing phone numbers or email addresses
* **Address Standardization**: Normalize consumer addresses

## Data Flow Through the Platform

### Inbound Data Flow (Source to MDM Hub)

1. **Data Extraction**: Data is extracted from source systems (databases, applications, files)
2. **Initial/Ongoing Load**: Data enters through either initial bulk load or ongoing incremental updates
3. **Data Staging**: Raw data is loaded into staging tables
4. **Data Quality Rules**: Validation rules are applied to check data quality
5. **Data Quality Strategies**: Comprehensive quality processing (standardization, parsing, enrichment) is performed
6. **External Enrichment**: Data is enriched using external services (address validation, business data append)
7. **Matching & Survivorship**: Duplicate records are identified, and golden records are created
8. **Security Check**: Data access permissions are validated
9. **MDM Hub Storage**: Master data is stored in the MDM Hub with full audit trail

### Outbound Data Flow (MDM Hub to Consumers)

1. **Master Data Views**: Golden records are exposed through optimized views
2. **Real-Time Events**: Changes trigger real-time event notifications
3. **Integrator**: Master data is pushed to external systems (Salesforce, Dynamics 365, etc.)
4. **APIs**: External systems pull master data via REST APIs
5. **Reports**: Business users access master data through BI tools and reports
6. **RDBMS Access**: Downstream systems query master data views directly

### User Interaction Flow

1. **Administration**: Administrators configure the platform through Studio
2. **Stewardship**: Data stewards manage data quality through FastApps
3. **Forms & Portal Applications**: Business users interact with master data through custom portals
4. **Workflow**: Changes flow through approval workflows as needed
5. **Presentation Views**: Users view formatted data through the UI
6. **Reports**: Users access insights through custom reports

## Multi-Domain Master Data Management

Profisee supports management of multiple master data domains within a single platform:

### Customer Domain

* **Customer Master**: Individual consumers and household data
* **Account Master**: Business accounts and organizations
* **Contact Master**: Points of contact within accounts
* **Hierarchies**: Customer-account relationships, household structures

### Product Domain

* **Product Master**: Product catalog with SKUs, descriptions, attributes
* **Product Hierarchies**: Category structures, brand hierarchies
* **Bill of Materials**: Product components and assemblies
* **Pricing**: Price lists and pricing rules

### Reference Domain

* **Code Lists**: Standard code tables (country codes, currency codes)
* **Lookup Values**: Domain-specific reference data
* **Standards**: Industry standard classifications
* **Cross-References**: Mappings between different coding systems

### Additional Domains

* **Supplier/Vendor Master**: Supply chain partner data
* **Location Master**: Stores, warehouses, facilities
* **Employee Master**: Workforce data
* **Asset Master**: Physical and digital assets
* **Financial Master**: Chart of accounts, cost centers, legal entities
* **Custom Domains**: Organization-specific master data domains

## Integration Patterns

### In-Scope vs. Client-Specific

The diagram distinguishes between standard platform capabilities and client-specific customizations:

* **In-Scope**: Standard Profisee components and features available to all customers out of the box
* **Client-Specific**: Custom reports, integrations, and configurations built for specific customer requirements

### Real-Time Integration

Profisee supports real-time, bi-directional integration with external systems:

* **Salesforce**: Sync customer and account data in real-time
* **Dynamics 365**: Keep master data synchronized with Microsoft Dynamics
* **Other Cloud Systems**: Integrate with any system offering REST or SOAP APIs
* **Event-Driven**: Trigger integrations based on data changes

### Batch Integration

For high-volume or scheduled data exchange:

* **File-Based**: Import/export CSV, XML, JSON files
* **Database Direct**: ETL from/to databases
* **Scheduled Jobs**: Run integrations on defined schedules

## Deployment Architecture Considerations

### Scalability

* **Horizontal Scaling**: Add more servers to handle increased load
* **Database Performance**: Optimized indexing and query patterns for millions of records
* **Caching**: Multi-level caching to reduce database load
* **Asynchronous Processing**: Background jobs for resource-intensive operations

### High Availability

* **Redundant Components**: Multiple instances of each service
* **Load Balancing**: Distribute traffic across servers
* **Database Replication**: Failover databases for disaster recovery
* **Health Monitoring**: Automatic detection and recovery from failures

### Security

* **Network Isolation**: Separate networks for different tiers
* **Encryption**: Data encrypted at rest and in transit
* **Secrets Management**: Secure storage of credentials and API keys
* **Penetration Testing**: Regular security assessments

## Best Practices for Implementation

### Data Modeling

* **Start Simple**: Begin with core entities and expand gradually
* **Business-Driven**: Model entities based on business concepts, not source systems
* **Reusable Components**: Create reusable attributes and domains
* **Future-Proof**: Design for extensibility

### Data Quality

* **Define Standards**: Establish clear data quality standards
* **Automated Rules**: Automate as much validation as possible
* **Human Review**: Reserve steward time for complex cases
* **Continuous Improvement**: Regularly refine rules based on results

### Governance

* **Clear Ownership**: Assign data stewards for each domain
* **Documented Processes**: Write down governance procedures
* **Training**: Train stewards on tools and processes
* **Metrics**: Track and report on data quality metrics

### Integration

* **Prioritize Sources**: Identify system of record for each attribute
* **Incremental Approach**: Connect systems one at a time
* **Error Handling**: Plan for integration failures
* **Monitoring**: Monitor integration health and performance

---