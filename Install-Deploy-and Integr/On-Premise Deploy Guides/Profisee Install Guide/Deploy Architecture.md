# Deployment Architecture

Understanding the major components and configuration options of Profisee Platform and related SQL Server components is important to plan your installation. This section identifies and defines the relevant components:

## Major Components

### Profisee Platform Cluster

Profisee Platform supports multi-node clusters consisting of one or more nodes for a high-availability architecture. At least one node must be configured, and additional nodes can be licensed. The additional nodes can be used for processing separate jobs, high-availability or failover.

Nodes must be hosted on a Physical or Virtual Machine running Windows Server 2016 or later operating system. The Virtual Machine can be hosted On-Premises in the customer's data center or in the customer's Cloud Tenant as Infrastructure-as-a-Service (IaaS). Azure is recommended but AWS and Google Cloud VMs are also supported.

Each node within a Profisee Cluster consists of Web Applications hosted in IIS, and a Windows Service. All services must be configured to run as an AD/Entra Service Account. The Windows Service runs on port 8003 by default, but can be configured on any free port. That port must be open in the firewall to allow for synchronization between the services.

### Profisee Database

The Profisee Database contains all master data records. It must be hosted on SQL Server 2017 or later Enterprise or Standard Edition, or any Platform-as-a-Service (PaaS) Cloud edition of SQL Server, like Azure SQL DB, Amazon RDS, etc. When using Azure SQL the vCore purchasing model is required.

It is recommended to have a dedicated SQL Server instance for the Profisee Database, and not a shared instance. If hosted on a shared instance performance of the Profisee Platform cannot be guaranteed. Profisee Platform uses default port 1433 to communicate with the Profisee Database. If the database is hosted in the Cloud you must ensure a high-speed, low-latency network connection is available between the Profisee Platform Cluster and Profisee Database. Profisee cannot support issues caused by slow or unstable network connectivity between the Profisee Cluster and Database. Hybrid Configurations where Profisee Platform is hosted on a Cloud VM with OnPrem SQL Server or Cloud SQL Server with OnPrem VM are not recommended.

### Profisee File Repository

The Profisee File Repository is used to host physical files such as Attachments, Subscribers, Workflows, etc. A single file repository is accessed and shared by all Profisee Cluster nodes, which is why it is recommended that the File Repository is hosted on a highly redundant Network Attached Storage or Cloud File Storage account. When a single node Profisee Cluster is configured, it is acceptable to host the File Repository on the same virtual machine as the node.

### FastApp Studio and Web Portal

The FastApp Studio is a client software application used for administering the Profisee Platform and configuring FastApps for data stewardship in the Web Portal. The client must be installed on a Physical or Virtual Machine running Windows 10 or later or Windows Server 2016 or later.

The Web Portal is used to provide web access to custom data stewardship web applications (FastApps) for business users to manage their Master Data. The Web Portal can be accessed by any modern browser including Microsoft Edge, Google Chrome, Mozilla Firefox, Apple Safari, etc. Microsoft Internet Explorer is not supported.

The Web Portal also provides access to the REST API Swagger page as well.

### Authentication Providers

For On-Premises deployment, where Profisee Cluster is configured on a Physical or Virtual Machine, that machine must be joined to a Domain and have access to Active Directory. For IaaS/Cloud VMs the machine must have access to an OpenID Connect (OIDC) authentication provider like Microsoft Entra, OKTA, Google, etc.

A Service Account user with minimum permissions to "Run as Service" and "Interactive Logon" to the machine must be provisioned to be configured in the Profisee Cluster for running all Web Applications and Windows Service.

A Windows Administrator user must be used as a Configuration Account. The Configuration Account can also be the Service Account if given Windows Administrator permissions. Local Windows Users are not supported. After Cluster configuration is complete, application users can be added.

### Data Governance

The Profisee Platform can integrate with Azure Purview for Data Governance. Azure Purview can be used with the Profisee Web Portal to provide data governance information about Assets, Lineage, Collections, etc. to Data Stewards. It also provides access to Profisee metadata in Purview.

### Configuration Options Summary

**Profisee Cluster:** Physical or Virtual Machines On-Premises **OR** Virtual Machines in Infrastructure-as-a-Service (IaaS) running Windows Server

**SQL Server:** On-Premises SQL Server **OR** Cloud SQL (vCore)

**File Repository:** On-Premises NAS **OR** Local Storage on VM (only for single node cluster) **OR** Azure File Storage

**Authentication:** On-Premises Active Directory **AND/OR** Open ID Connect (OIDC) Authentication Provider

**Governance:** None **OR** Azure Purview

**Users:**Physical or virtual machines running Windows or Windows Server

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-if967e143fe503381.png)

### High-Availability Clusters

High availability is achieved by providing failover at the database tier and the Web application tier. Use a Profisee cluster with multiple nodes in conjunction with network load-balancers to support high-availability configurations. Each node in a HA configuration must be licensed separately.

When running on premise, a SQL Server AlwaysOn Availability Group provides high-availability at the database tier. When running on Azure, Azure SQL DB inherently provides high-availability.

Note that some processes are highly stateful and must be reconfigured (manual or automated) to run on another node when the designated processing node is down and failover is required. These processes include:

-Matching and survivorship
-Event processing
-Workflows