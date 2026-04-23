# External Systems List Overview

The external systems list provides a way for non-Profisee systems to share data with Profisee while continuing to keep track of members using system-specific IDs. The external list plays a key role in making Profisee the centralized hub for your master data information.

An external systems list is available for each Profisee server. After external systems are associated with the server using this list, it is possible to create system-aware text attributes in Profisee models. These attributes store as strings the proprietary identifiers from external systems (such as Salesforce or Dynamics). Using event processing, the identifying attributes from external systems can then be copied into these system-aware attributes. They preserve the proprietary format IDs for external members when external data enters the Profisee system.This makes it possible for Profisee and external systems to identify members accurately without creating duplicates on any system.

In this way, data can be shared between Profisee and systems using different methods of creating member IDs. Profisee will keep track of members using Profisee code values, while, for example, the Salesforce system continues to identify members using the Salesforce ID.

Configure the external systems list as part of event processing configuration:

1. [Add external systems to the list (Edit)](https://support.profisee.com/wikis/profiseeplatform/edit_the_external_systems_list)
2. [Create system-identity attributes in the model](https://support.profisee.com/wikis/profiseeplatform/create_system_identity_attributes_using_adaptive_modeling)
3. [Configure external data transfers with Profisee as the target server](https://support.profisee.com/wikis/profiseeplatform/configure_external_data_transfers_with_profisee_as_the_target_server)

The Profisee external systems list must be configured with external systems in order for you to complete event processing configuration for external systems.