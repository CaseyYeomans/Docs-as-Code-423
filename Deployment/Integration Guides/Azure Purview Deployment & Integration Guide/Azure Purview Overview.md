# Azure Purview Overview

## What is Purview?

Purview is a data governance solution that provides broad visibility of customers' on-premise and cloud data estates. It offers a combination of data discovery and classification, lineage, metadata search and discovery, and analytics that identify data usage across the enterprise. Purview is deployed as a PaaS solution in customers' Azure subscriptions. Profisee has been enhanced to allow metadata associated with your master data service model to be published to Purview and to be able to read the enriched metadata from Purview allowing data stewards to benefit from enterprise governance processes and policies.

### Profisee Integration Overview

Profisee's integration with Purview includes the following features:

- Azure ARM template capabilities that allow dev-ops teams to deploy Profisee with Azure Purview and to identify connection information allowing the Profisee Platform to connect to the customer's Purview account.
- On-premise deployment via the Profisee Configuration Manager allows for configuring connectivity to the customer's Purview account running in their Azure subscription.
- Connectivity and synchronization capabilities that automatically registers a Profisee instance (i.e. installation) and publishes model metadata to Purview as master data modeling occurs in Profisee. This includes publishing and synchronization of the following solution artifacts:

- **Profisee Instance**: Provides the properties of the Profisee installation so that Purview users have global visibility to all Profisee instance that have been installed across the customer's IT landscape.
- **Profisee Entities**: Provides the properties of all master data entities that have been created in the Profisee database associated with the installed instance.
- **Profisee Attributes**: Provides the properties of all data attributes (aka columns) associated with the entities that have been published.
- **Profisee Relationships**: Provides the properties of all the relationships defined between entities for all three attribute types (ParentChild, Recursive, and Many to Many).
- **Profisee Hierarchies**: Provides the properties of all hierarchies that have been created in Profisee.

- Governance data visibility in Profisee's FastApp Portal for the solution artifacts that published to Purview. A **Governance Dialog** presents details related to the master data model including enriched governance data in terms of metadata categorization, glossary terms, resources, as well as contacts (i.e. data owners and experts). This information is available from the**Help** menu as well as from entity grids and forms that allow data stewards to better understand the data they are managing.

These capabilities provide data stewards working in Profisee with greater insight into the definition, ownership, and subject matter expertise related to the data the stewards are charged with managing.

### See more

- [Prerequisites for Integrating with Purview](https://support.profisee.com/wikis/profiseeplatform/prerequisites_for_integrating_with_purview)
- [Deploying Purview in an Azure PaaS Environment](https://support.profisee.com/wikis/profiseeplatform/deploying_the_purview_preview_in_an_azure_paas_environment)
- [Validating Your Purview Connectivity](https://support.profisee.com/wikis/profiseeplatform/validating_your_purview_connectivity)
- [Profisee Metadata Publishing Details](https://support.profisee.com/wikis/profiseeplatform/profisee_metadata_publishing_details)
- [Viewing Purview Governance Information in FastApp Portal](https://support.profisee.com/wikis/profiseeplatform/viewing_purview_governance_information_in_fastapp_portal)