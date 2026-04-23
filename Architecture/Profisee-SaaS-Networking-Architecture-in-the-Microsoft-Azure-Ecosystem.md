# Profisee SaaS Networking Architecture in the Microsoft Azure Ecosystem

## Overview

Profisee's Software-as-a-Service (SaaS) platform is architected as a comprehensive, multi-tenant solution within the Microsoft Azure ecosystem. The networking architecture is designed to provide secure, scalable, and highly available master data management capabilities while seamlessly integrating with customers' existing Azure infrastructure, Microsoft services, and external cloud platforms.

This architecture document explains the networking topology, security boundaries, authentication flows, data paths, and integration patterns that enable Profisee to deliver enterprise-grade MDM as a managed service.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i62200ce2f936551e.png)

## Infrastructure Boundaries and Tenancy Model

### Profisee SaaS Infrastructure Boundary

The Profisee SaaS infrastructure operates within its own boundary at **profiseecloud.com**, providing:

* **Multi-Tenant Isolation**: Each customer's Profisee instance runs in isolated containers within the Kubernetes cluster
* **Shared Infrastructure**: Core services like Traffic Manager, Application Gateway, and Kubernetes clusters are shared across tenants
* **Regional Deployment**: Infrastructure is deployed in paired Azure regions for high availability and disaster recovery
* **Managed Security**: Profisee manages all infrastructure security, patching, and updates

### Customer Tenant Integration

Customers maintain their own Azure tenants that integrate with Profisee through secure connectivity:

* **Microsoft Entra ID (Azure AD)**: Customer identity and authentication services
* **Resource Groups**: Customer-owned Azure resources that interact with Profisee
* **Private Connectivity**: Private links and virtual network peering enable secure, non-public connections
* **Bring Your Own Resources**: Customers can leverage their own Azure services (SQL DB, Data Factory, Functions, Logic Apps, Databricks, etc.)

## Network Architecture Components

### Traffic Management and Global Distribution

#### Traffic Manager

Azure Traffic Manager serves as the global DNS-based load balancer:

* **Entry Point**: All user and API requests enter through Traffic Manager
* **Health Monitoring**: Continuously monitors endpoint health in both Primary and Failover regions
* **Automatic Failover**: Redirects traffic to the Failover region if the Primary becomes unavailable
* **Routing Policies**: Supports priority, performance, geographic, and weighted routing
* **DNS Resolution**: Resolves profiseecloud.com to the appropriate regional endpoint

### Regional Infrastructure (Primary and Failover)

Profisee deploys identical infrastructure in paired Azure regions to provide high availability and disaster recovery capabilities.

#### Application Gateway

* **Layer 7 Load Balancer**: Application-level traffic distribution and routing
* **Web Application Firewall (WAF)**: Protects against OWASP Top 10 vulnerabilities and web attacks
* **SSL/TLS Termination**: Handles HTTPS encryption and certificate management
* **URL-Based Routing**: Routes requests to appropriate backend services based on URL patterns
* **Session Affinity**: Maintains user sessions to specific Profisee instances

#### Azure Firewall

* **Network Security**: Stateful packet inspection and filtering
* **Outbound Protection**: Controls traffic leaving the Profisee environment
* **Threat Intelligence**: Filters traffic based on Microsoft threat intelligence feeds
* **Centralized Logging**: All network traffic is logged for security monitoring and compliance
* **FQDN Filtering**: Controls access to external services by domain name

#### Load Balancer

* **Layer 4 Distribution**: TCP/UDP load balancing to Kubernetes nodes
* **Health Probes**: Monitors node health and removes unhealthy nodes from rotation
* **High Availability**: Distributes traffic across multiple availability zones
* **Internal Load Balancing**: Routes traffic within the virtual network

### Kubernetes Infrastructure

Profisee runs on Azure Kubernetes Service (AKS) with dedicated node pools for different workload types.

#### Linux Node Pool

Hosts the ingress infrastructure across multiple availability zones:

* **Ingress Controllers**: NGINX-based controllers that manage external access to Profisee services
* **Multi-Zone Distribution**: Nodes are spread across 3 availability zones within each region
* **Automatic Scaling**: Node pool scales based on CPU and memory utilization
* **High Availability**: Multiple ingress controller replicas ensure continuous availability

#### Windows Node Pool

Hosts the Profisee application instances across availability zones:

* **Profisee Servers**: Windows containers running Profisee application instances
* **Instance Isolation**: Each customer's Profisee instance runs in isolated containers
* **Multi-Zone Deployment**: Instances are distributed across availability zones
* **Pod Scheduling**: Kubernetes schedules pods across nodes for optimal resource utilization

### Data Services

#### Storage Resources

Each customer has dedicated storage resources:

* **Database**: Azure SQL Database for Profisee master data
* **File Repository**: Azure Storage for file attachments and documents
* **Mirroring**: Data is mirrored to the failover region
* **Read-Only Replica**: Failover region has read-only access during normal operations
* **Failover Promotion**: Storage can be promoted to read-write in disaster scenarios

#### Virtual Network

* **Network Isolation**: Each Profisee region operates within its own virtual network
* **Private Endpoints**: Secure connections to Azure services without public internet exposure
* **Network Security Groups**: Fine-grained control over network traffic
* **Service Endpoints**: Optimized connectivity to Azure PaaS services

## Authentication and Identity Management

### Microsoft Entra ID (Azure AD) Integration

Profisee integrates with customer Azure AD tenants for authentication:

* **Single Sign-On (SSO)**: Users authenticate using their corporate credentials
* **OAuth 2.0/OpenID Connect**: Industry-standard authentication protocols
* **Multi-Factor Authentication (MFA)**: Supports customer MFA policies
* **Conditional Access**: Honors customer conditional access policies
* **Role-Based Access Control (RBAC)**: Azure AD groups map to Profisee roles

### External OIDC Authentication Services

Profisee supports external identity providers:

* **Okta**: Enterprise identity and access management
* **Google**: Google Workspace authentication
* **Ping Identity**: Federated identity services
* **Other OIDC Providers**: Any OpenID Connect-compliant identity provider

### Authentication Service

The Profisee Authentication Service manages identity and access:

* **Token Management**: Issues and validates access tokens
* **Session Management**: Maintains user sessions across the platform
* **Identity Federation**: Bridges external identity providers with Profisee services
* **API Authentication**: Validates API calls using bearer tokens

## Inbound Request Flows

### User Access Flow

When users access Profisee, requests follow this path:

1. **User Initiates Connection**: User navigates to their Profisee instance URL
2. **Traffic Manager Resolution**: DNS resolves to the active regional endpoint
3. **Application Gateway**: Receives the HTTPS request and performs WAF inspection
4. **Azure Firewall**: Applies network security policies
5. **Load Balancer**: Routes to a healthy Kubernetes node
6. **Ingress Controller**: Routes to the appropriate Profisee instance container
7. **Profisee Instance**: Serves the request from the Windows node pool

### Azure Tenant Authentication Flow

When authentication is required:

1. **User Access Request**: User attempts to access Profisee without valid session
2. **Redirect to Azure AD**: Profisee redirects to customer's Azure AD tenant
3. **User Authentication**: User authenticates with corporate credentials (and MFA if required)
4. **Token Issuance**: Azure AD issues access tokens to Profisee
5. **Token Validation**: Profisee Authentication Service validates the token
6. **Session Creation**: Profisee creates an authenticated session
7. **Access Granted**: User gains access to their Profisee instance

### Profisee Instance Authentication Flow

API calls to Profisee instances follow authentication:

1. **API Request**: External system calls Profisee REST API
2. **Bearer Token Validation**: Profisee validates the OAuth bearer token
3. **Azure Firewall Check**: Network-level security validation
4. **REST API Gateway**: Routes request to appropriate microservice
5. **Authorization Check**: Verifies user/service permissions
6. **Request Processing**: Backend service processes the request
7. **Response Return**: Result is returned through the same path

### Global Services Request Flow

Profisee global services handle cross-instance operations:

* **Profisee Knowledge Search**: AI-powered documentation search
* **Doc Search Function**: Azure Function for document indexing and retrieval
* **Fabric Integration Services**: Microsoft Fabric connectors and workloads
* **Elastic Job Agents**: Scheduled background jobs across instances

## Outbound Request Flows

### External Service Requests

Profisee instances connect to external services through controlled paths:

* **Azure Firewall**: All outbound traffic passes through the firewall for inspection and logging
* **FQDN Filtering**: Only approved external services are accessible
* **Threat Protection**: Outbound connections are checked against threat intelligence
* **Logging**: All external connections are logged for security audit

### Customer Tenant Connections

Profisee connects to customer Azure resources:

#### Private Link Requests

* **Private Endpoints**: Secure, private connections to customer Azure services
* **No Public Internet**: Traffic never traverses the public internet
* **Virtual Network Integration**: Direct network connectivity between Profisee and customer resources
* **DNS Resolution**: Private DNS zones resolve service endpoints correctly

#### Supported Customer Services

* **Azure SQL DB**: Direct connections to customer databases
* **Azure Data Factory**: Trigger and monitor data pipelines
* **Azure Databricks**: Execute notebooks and jobs
* **Azure Functions**: Invoke serverless functions
* **Azure Logic Apps**: Trigger workflow automations
* **Azure Service Bus**: Publish and consume messages
* **Azure AI Services**: Call cognitive services APIs
* **Azure Key Vaults**: Retrieve secrets and certificates

### Authentication and Token Requests

Outbound authentication flows:

* **Azure AD Token Acquisition**: Profisee services obtain tokens to call customer APIs
* **Managed Identity**: Profisee uses managed identities where possible
* **Service Principal**: Customer provides service principals for secure access
* **Certificate-Based Auth**: Some integrations use certificate authentication

## Integration with Microsoft Services

### Microsoft Fabric Integration

Profisee integrates deeply with Microsoft Fabric:

#### Fabric Connector

* **Native Connector**: Purpose-built connector for Fabric data pipelines
* **Profisee Workload**: Custom Fabric workload for master data management
* **Warehouse & Lakehouse**: Direct connectivity to Fabric data stores
* **Multi-Tenant Support**: Customers can have multiple Fabric tenants

#### Data Flow

* **Master Data Publishing**: Profisee publishes curated master data to Fabric
* **Lakehouse Integration**: Master data stored in OneLake for analytics
* **Real-Time Sync**: Near real-time data synchronization
* **Delta Tables**: Efficient storage using Delta Lake format

### Microsoft Purview Integration

Profisee integrates with Purview for data governance:

#### Purview Connector

* **Collections**: Profisee assets organized into Purview collections
* **Data Catalog**: Profisee entities published to Purview data catalog
* **Lineage Tracking**: Data lineage from source systems through Profisee to downstream consumers
* **Private Link**: Secure connectivity via private endpoints

#### Governance Workflows

* **User Resolution Requests**: Stewardship team handles data quality issues
* **Publishing**: Profisee publishes metadata and lineage to Purview
* **Queries**: Users discover Profisee assets through Purview catalog
* **Microsoft Graph API**: Integration via Graph API for unified governance

### Office 365 Integration

Profisee integrates with Office 365 services:

#### Bot Connector Service

* **Azure Bot Service**: Manages bot conversations and channels
* **Profisee Bot Extension**: Custom bot for Teams integration
* **Multi-Tenant Support**: Each customer has their own O365 tenant configuration

#### Adaptive Cards Integration

* **Teams Notifications**: Data quality alerts and workflow approvals in Teams
* **Interactive Cards**: Users can respond to data stewardship tasks directly in Teams
* **Share to Teams**: Profisee records can be shared as adaptive cards
* **Collaboration**: Teams becomes a collaboration layer for master data management

## External Cloud and Line-of-Business Integrations

### Supported External Services

Profisee Connect Service integrates with numerous external platforms:

#### Data Platforms

* **Snowflake**: Data warehouse integration for master data distribution
* **Salesforce**: CRM integration for customer and account master data
* **Databricks**: Spark-based analytics on master data

#### Identity and Data Services

* **Okta**: Enterprise identity and SSO
* **Google**: Google Workspace and Cloud Platform integration
* **Ping Identity**: Federated identity management

#### Data Quality and Enrichment

* **Melissa**: Address verification and geocoding
* **Loqate**: Global address validation
* **Dun & Bradstreet**: Business intelligence and data enrichment

#### API Management

* **REST APIs**: Standard REST API integrations
* **API Keys**: Secure API key management
* **OAuth**: OAuth 2.0 for authenticated API access

### External Master Data Consumers

External systems consume master data from Profisee:

* **Direct API Access**: RESTful APIs for retrieving master data
* **Webhook Subscriptions**: Real-time notifications of master data changes
* **Batch Exports**: Scheduled exports of master data to external systems
* **File-Based Integration**: CSV, XML, or JSON file exports

## Profisee Platform Microservices Architecture

Each Profisee instance runs as a set of microservices within the Kubernetes cluster:

### User-Facing Services

#### REST API Gateway

* **API Management**: Centralized API gateway for all REST endpoints
* **Rate Limiting**: Protects backend services from overload
* **Authentication**: Validates tokens and manages API keys
* **Request Routing**: Routes API calls to appropriate microservices
* **SignalR Support**: Real-time web socket connections for live updates

#### FastApp Portal

* **Web UI**: Modern, responsive web application for data stewardship
* **User Experience**: Business-user friendly interface for master data management
* **Shared Services**: Leverages common services for authentication, data access, etc.

### Core Data Services

#### Data Service

* **Master Data CRUD**: Create, read, update, delete operations on master data
* **Query Processing**: Efficient querying of large master data sets
* **Caching**: In-memory caching for performance
* **Database Interaction**: Manages connections to Azure SQL Database

#### Modeling Service

* **Entity Management**: Define and manage master data entities
* **Attribute Configuration**: Configure entity attributes and data types
* **Relationship Definition**: Define relationships between entities
* **Hierarchy Management**: Create and maintain data hierarchies

### Data Quality and Governance Services

#### Matching Service

* **Duplicate Detection**: Identifies potential duplicate records using fuzzy matching algorithms
* **Matching Rules**: Configurable matching rules and thresholds
* **Machine Learning**: ML-powered matching for improved accuracy
* **Match Review**: Workflow for data stewards to review and confirm matches

#### Governance Service

* **Data Quality Rules**: Define and enforce data quality validation rules
* **Business Rules**: Custom business logic for data validation
* **Compliance Tracking**: Monitor compliance with data governance policies
* **Audit Logging**: Complete audit trail of all data changes

#### Workflow Service

* **Approval Workflows**: Route data changes through approval processes
* **Task Management**: Assign and track data stewardship tasks
* **Notifications**: Alert users of pending tasks and workflow events
* **Escalation**: Automatic escalation of overdue tasks

### Integration and AI Services

#### Connect Service

* **External Integration**: Manages connections to external systems
* **Service Provider Framework**: Extensible framework for custom integrations
* **Data Import/Export**: Orchestrates data movement to and from external systems
* **Transformation**: Data mapping and transformation during integration

#### Aisey Chatbot Service

* **AI-Powered Assistance**: Natural language interaction with Profisee
* **Knowledge Search**: Searches Profisee documentation and help content
* **Azure AI Integration**: Leverages Azure OpenAI and Cognitive Services
* **Context-Aware**: Understands user context and provides relevant assistance

### Supporting Services

#### File Attachments Service

* **Document Management**: Attach files and documents to master data records
* **Azure Blob Storage**: Stores files in Azure Storage
* **Version Control**: Maintains file versions and history
* **Access Control**: Enforces permissions on file access

#### Monitor Service

* **System Health**: Monitors Profisee instance health and performance
* **Metrics Collection**: Collects application metrics and telemetry
* **Alerting**: Triggers alerts for system issues
* **Dashboard**: Provides visibility into system status

#### Shared Services

All microservices leverage shared services for common functionality:

* **Configuration Management**: Centralized configuration
* **Logging**: Structured logging to Azure Monitor
* **Caching**: Distributed caching layer
* **Service Discovery**: Kubernetes-based service discovery

## Profisee Knowledge Search Architecture

Profisee Knowledge Search provides AI-powered documentation assistance:

### Components

* **Doc Search Function**: Azure Function that processes search queries
* **Azure AI Search**: Cognitive Search service for full-text search and semantic understanding
* **BLOB Storage**: Stores documentation content and indexes
* **Azure AI**: OpenAI and Cognitive Services for natural language understanding

### Search Flow

1. **User Query**: User asks a question in Aisey Chatbot
2. **Function Invocation**: Doc Search Function is called with the query
3. **Semantic Search**: Azure AI Search performs semantic search across documentation
4. **AI Enhancement**: Azure OpenAI generates contextual responses
5. **Result Return**: Relevant documentation and AI-generated answers returned to user

## High Availability vs. Disaster Recovery

### High Availability (Within Region)

High availability protects against component and availability zone failures:

* **Multi-Zone Deployment**: Kubernetes nodes distributed across 3 availability zones
* **Multiple Pod Replicas**: Each microservice runs multiple replicas
* **Health Monitoring**: Kubernetes automatically restarts failed pods
* **Load Balancing**: Traffic distributed across healthy nodes
* **Zone Failure**: If one zone fails, traffic shifts to remaining zones automatically

### Disaster Recovery (Cross-Region)

Disaster recovery protects against regional failures:

* **Paired Regions**: Primary and Failover regions in Azure paired regions
* **Data Replication**: Database and storage mirrored to failover region
* **Read-Only Replica**: Failover region maintains read-only copy during normal operations
* **Automatic Failover**: Traffic Manager detects regional failure and redirects traffic
* **Promotion**: Failover region promoted to read-write when primary fails
* **Regional Failure**: Entire regional infrastructure fails, but service continues from failover region

## Security Architecture

### Network Security

* **Defense in Depth**: Multiple security layers from edge to application
* **WAF Protection**: Web Application Firewall at Application Gateway
* **Network Firewall**: Azure Firewall for network-level protection
* **Network Segmentation**: Virtual networks and subnets isolate components
* **Private Endpoints**: Eliminates public internet exposure for Azure services

### Identity and Access Management

* **Azure AD Integration**: Enterprise identity management
* **RBAC**: Role-based access control throughout the platform
* **Managed Identities**: Eliminates credential management
* **Conditional Access**: Enforce customer security policies
* **MFA Support**: Multi-factor authentication required when configured

### Data Protection

* **Encryption at Rest**: All data encrypted in Azure Storage and SQL Database
* **Encryption in Transit**: TLS 1.2+ for all network communications
* **Key Management**: Azure Key Vault for cryptographic key storage
* **Data Isolation**: Customer data logically separated in multi-tenant architecture

### Compliance and Auditing

* **Audit Logging**: Comprehensive logging of all data access and changes
* **Azure Monitor**: Centralized logging and monitoring
* **Compliance Certifications**: SOC 2, GDPR, HIPAA compliance
* **Data Residency**: Data stored in customer-selected geographic regions

## Network Performance Optimization

### Caching Strategies

* **Application-Level Caching**: In-memory caching within microservices
* **Distributed Cache**: Shared cache across Profisee instances
* **CDN**: Azure CDN for static content delivery
* **Database Query Caching**: Frequently accessed data cached

### Connection Pooling

* **Database Connection Pools**: Efficient database connection reuse
* **HTTP Connection Reuse**: Persistent connections to external services
* **Azure Service Bus**: Message queuing for asynchronous operations

### Regional Proximity

* **Geo-Distributed**: Profisee deployed in multiple Azure regions worldwide
* **Low Latency**: Users connect to geographically close data centers
* **Traffic Manager Routing**: Performance-based routing to optimal region

## Operational Considerations

### Monitoring and Observability

* **Azure Monitor**: Centralized monitoring for all Azure resources
* **Application Insights**: Application performance monitoring and diagnostics
* **Log Analytics**: Query and analyze logs across all services
* **Metrics and Dashboards**: Real-time visibility into system health
* **Alerting**: Proactive alerts for issues and anomalies

### Capacity Management

* **Auto-Scaling**: Kubernetes automatically scales based on demand
* **Resource Quotas**: Each customer has defined resource limits
* **Performance Monitoring**: Track resource utilization trends
* **Capacity Planning**: Proactive planning based on growth projections

### Update and Maintenance

* **Rolling Updates**: Kubernetes performs zero-downtime updates
* **Blue-Green Deployments**: Test updates before switching traffic
* **Rollback Capability**: Quick rollback if issues are detected
* **Maintenance Windows**: Scheduled maintenance with customer notification

## Integration Best Practices

### Customer Azure Resource Integration

* **Private Link**: Always use private endpoints when possible for security
* **Managed Identity**: Use managed identities instead of service principals
* **Network Security Groups**: Configure NSGs to allow only necessary traffic
* **Service Tags**: Use Azure service tags for firewall rules

### External Service Integration

* **OAuth 2.0**: Prefer OAuth over API keys for authentication
* **Webhook Security**: Validate webhook signatures
* **Rate Limiting**: Respect rate limits of external services
* **Error Handling**: Implement retry logic with exponential backoff

### Data Integration Patterns

* **Real-Time**: Use event-driven integration for time-sensitive data
* **Batch**: Schedule batch jobs for large data volumes
* **Incremental**: Only transfer changed data to minimize bandwidth
* **Idempotency**: Ensure operations can be safely retried

---

### Full Networking Diagrams

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3319fdaba2a2329b.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i35a72fa9c5893e6.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i99a385d12b7347ee.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ibbcd787c56463b1f.png)