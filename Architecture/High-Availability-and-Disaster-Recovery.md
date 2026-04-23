# High Availability and Disaster Recovery

---

# Profisee SaaS High Availability and Disaster Recovery

## Overview

Profisee's SaaS deployment architecture is designed to deliver enterprise-grade reliability, availability, and disaster recovery capabilities. This multi-region architecture ensures that the Profisee platform remains accessible and operational even in the face of regional outages, providing customers with peace of mind and continuous access to their master data management solutions.

The architecture spans two Azure regions—Australia Southeast (Primary) and Australia East (Secondary)—and implements multiple layers of redundancy, automated failover, and data replication to achieve high availability.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic65d83d189c61f6b.png)

## Architecture Components

### Traffic Distribution and Routing

#### Traffic Manager

Azure Traffic Manager serves as the global entry point for all Profisee SaaS users:

* **DNS-Based Load Balancing**: Directs user requests to the optimal region based on health, performance, or priority routing policies
* **Automatic Failover**: Continuously monitors regional endpoints and automatically redirects traffic to the healthy region if the primary becomes unavailable
* **Geographic Distribution**: Can route users to the nearest region for optimal performance in active-active configurations

## Regional Infrastructure

Both Australia Southeast and Australia East regions implement identical infrastructure patterns, ensuring consistent performance and enabling seamless failover between regions.

### Network Security and Load Balancing Layers

Each region implements a three-tier network security and load balancing architecture:

#### Application Gateway

* Layer 7 (application-level) load balancer with Web Application Firewall capabilities
* SSL/TLS termination for secure HTTPS connections
* URL-based routing to direct requests to appropriate services
* Protection against common web vulnerabilities (OWASP Top 10)

#### Load Balancer

* Distributes incoming traffic across Kubernetes nodes
* Performs health checks to ensure traffic only reaches healthy nodes
* Provides high availability for the Kubernetes cluster endpoints

#### Firewall

* Azure Firewall provides stateful packet inspection
* Enforces network security policies between components
* Filters outbound traffic from the Kubernetes cluster
* Logs all network activity for security monitoring and compliance

### Kubernetes Infrastructure

Each region runs Profisee on Azure Kubernetes Service (AKS) with dedicated node pools for different workload types.

#### Linux Node Pool

The Linux Node Pool hosts the ingress infrastructure:

* **Ingress Controllers**: NGINX-based ingress controllers manage external access to Profisee services within the Kubernetes cluster
* **Multiple Nodes**: Node 1 through Node N provide horizontal scaling and redundancy
* **Availability Zones**: Nodes are distributed across multiple Azure Availability Zones within each region to protect against datacenter-level failures

#### Windows Node Pool

The Windows Node Pool hosts the Profisee application containers:

* **Profisee Containers**: The Profisee platform runs in Windows containers across multiple nodes
* **Multi-Zone Distribution**: Containers are scheduled across availability zones for maximum uptime
* **Scalability**: Node 1 through Node N allows the cluster to scale horizontally based on demand
* **High Availability**: If a node or zone fails, Kubernetes automatically reschedules containers to healthy nodes

## Shared Infrastructure and Data Services

### Azure Key Vault

Azure Key Vault provides centralized secrets management across both regions:

* **Geo-Replicated**: Secrets, keys, and certificates are automatically replicated between regions
* **High Availability**: Both regions can access Key Vault even if one region experiences an outage
* **Secure Storage**: Stores database connection strings, API keys, certificates, and other sensitive configuration data
* **Access Control**: Kubernetes pods use managed identities to securely retrieve secrets without embedding credentials in code

### GRS Fileshare (Geo-Redundant Storage)

Geo-Redundant Storage provides replicated file storage across regions:

* **Primary Region Access**: The Fileshare in Australia Southeast serves as the primary read-write storage
* **GRS Replication**: Data is automatically and asynchronously replicated to the Australia East region
* **Disaster Recovery**: In a failover scenario, the secondary fileshare can be promoted to read-write mode
* **Shared Data**: Stores files, documents, and assets that need to be accessible across the Profisee platform

### SQL Database with Failover Group

The database tier implements active geo-replication for business continuity:

#### Primary SQL Database (Australia Southeast)

* Hosts the primary Profisee database with read-write access
* Deployed across multiple availability zones for local high availability
* Handles all write operations during normal operations
* Connected to the Kubernetes cluster via virtual network for secure, low-latency access

#### Secondary SQL Database (Australia East)

* Maintains a continuously synchronized replica of the primary database
* Also deployed across availability zones for redundancy
* Can serve read-only queries to offload the primary database
* Ready to be promoted to primary during failover events

#### SQL Failover Group

* **Automatic Failover**: Monitors the primary database and automatically initiates failover if it becomes unavailable
* **Connection String Management**: Provides listener endpoints that automatically redirect connections to the current primary database
* **Configurable Policies**: Allows customization of failover triggers and grace periods
* **Data Synchronization**: Ensures the secondary database maintains a current copy of all data

### Virtual Network Integration

Both regions utilize virtual networks to provide secure, private connectivity:

* **Network Isolation**: Resources communicate over private networks rather than the public internet
* **Cross-Region Connectivity**: Virtual network peering or VPN gateways enable secure communication between regions
* **Service Endpoints**: Private endpoints for SQL Database and Storage ensure data never traverses public networks

## High Availability Strategy

### Multi-Zone Redundancy

Each region leverages Azure Availability Zones to provide infrastructure redundancy:

* **Datacenter Independence**: Availability zones are physically separate datacenters within a region
* **Kubernetes Node Distribution**: Both Linux and Windows nodes are spread across zones
* **Database Redundancy**: SQL databases use zone-redundant configurations
* **Automatic Recovery**: If one zone fails, workloads automatically shift to healthy zones

### Regional Redundancy

The dual-region architecture protects against regional failures:

* **Active-Passive Configuration**: Typically, Australia Southeast serves as the active region while Australia East stands ready as passive
* **Can Run Active-Active**: Both regions can simultaneously serve traffic for load distribution and reduced latency
* **Independent Infrastructure**: Each region has complete, independent infrastructure to handle full production load

## Disaster Recovery Capabilities

### Recovery Time Objective (RTO)

The time required to restore service after a disaster:

* **Zone Failure**: Near-zero RTO—Kubernetes automatically reschedules pods to healthy zones within seconds
* **Regional Failure**: Typically 5-15 minutes for automated failover, depending on monitoring intervals and failover policies
* **Traffic Manager**: Redirects traffic based on endpoint health checks (typically 30-60 seconds)
* **SQL Failover Group**: Database failover completes within minutes

### Recovery Point Objective (RPO)

The maximum acceptable data loss measured in time:

* **SQL Database**: Near-zero RPO—continuous replication ensures minimal data loss (typically seconds)
* **GRS Fileshare**: RPO of approximately 15 minutes due to asynchronous replication
* **Configuration Data**: Key Vault replication is nearly instantaneous

### Failover Scenarios

#### Scenario 1: Availability Zone Failure

* Kubernetes detects unhealthy nodes in the failed zone
* Pods are automatically rescheduled to nodes in healthy zones
* Load balancers stop sending traffic to failed zone
* Users experience minimal to no service interruption

#### Scenario 2: Regional Failure

* Traffic Manager health probes detect primary region unavailability
* Traffic is automatically routed to the secondary region (Australia East)
* SQL Failover Group promotes the secondary database to primary
* GRS Fileshare in secondary region becomes accessible
* Profisee platform continues operating from the secondary region

#### Scenario 3: Planned Maintenance

* Traffic is manually drained from one region via Traffic Manager
* Maintenance and updates are applied to the drained region
* Region is validated and returned to service
* Process is repeated for the second region
* Zero-downtime maintenance is achieved

## Security and Compliance

### Defense in Depth

The architecture implements multiple security layers:

* **Application Gateway WAF**: Protects against web application attacks
* **Azure Firewall**: Controls network traffic and enforces security policies
* **Network Isolation**: Virtual networks separate and secure different components
* **Private Endpoints**: Database and storage access never uses public internet
* **Key Vault**: Centralized, encrypted secrets management
* **Managed Identities**: Eliminates the need for storing credentials in configuration

### Data Protection

* **Encryption at Rest**: All data in SQL Database and Storage is encrypted
* **Encryption in Transit**: TLS/SSL for all network communications
* **Geo-Replication**: Data is replicated to protect against regional disasters
* **Backup and Restore**: Automated backups with point-in-time restore capabilities

## Operational Excellence

### Monitoring and Alerting

Comprehensive monitoring ensures proactive issue detection:

* Azure Monitor tracks infrastructure and application metrics
* Traffic Manager monitors endpoint health across both regions
* Kubernetes metrics provide insight into cluster and pod health
* SQL Database monitoring tracks replication lag and performance
* Application Insights monitors Profisee application performance and errors
* Automated alerts notify operations teams of issues before users are impacted

### Automated Operations

* **Auto-Scaling**: Kubernetes automatically scales pods based on CPU and memory usage
* **Self-Healing**: Kubernetes restarts failed containers and reschedules pods from unhealthy nodes
* **Automated Failover**: No manual intervention required for most failure scenarios
* **Patch Management**: Automated updates for Kubernetes, operating systems, and Azure services

## Performance Optimization

### Regional Proximity

* Australia Southeast and Australia East are geographically close, minimizing replication latency
* Users can be routed to the nearest region for optimal response times
* Low-latency replication ensures data consistency across regions

### Caching and CDN

* Static assets can be cached at Application Gateway level
* Azure CDN can be integrated for global content distribution
* Database read replicas can offload read-heavy workloads

## Business Continuity Benefits

This architecture provides Profisee SaaS customers with:

* **99.99% Availability SLA**: Multi-zone and multi-region redundancy supports high availability targets
* **Minimal Data Loss**: Continuous replication ensures RPO measured in seconds
* **Fast Recovery**: Automated failover delivers RTO measured in minutes
* **Zero-Downtime Maintenance**: Updates can be applied without service interruption
* **Geographic Redundancy**: Protection against natural disasters or regional outages
* **Scalability**: Infrastructure can grow to meet increasing demand
* **Enterprise-Grade Security**: Multiple security layers protect data and applications

## Comparison with On-Premises Deployments

Profisee SaaS architecture advantages over traditional on-premises deployments:

* **Automated Disaster Recovery**: No manual failover procedures or recovery plans to maintain
* **Continuous Updates**: Always running the latest Profisee version with minimal downtime
* **Global Infrastructure**: Leverages Azure's worldwide datacenter network
* **Reduced Operational Burden**: Profisee manages infrastructure, patching, and monitoring
* **Elastic Scalability**: Resources scale automatically based on demand
* **Cost Predictability**: Subscription-based pricing with no capital expenditure

---