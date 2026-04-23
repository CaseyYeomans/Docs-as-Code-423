# System Aware Identity Management (SAIM) Overview

System Aware Identity Management (SAIM) provides a method of identifying data members across multiple systems without the need to create duplicates. Profisee Server acts as a central hub, controlling the tracking for all members and providing attributes to track and identify the same members as they exist on multiple different systems.

Tracking members across disparate systems, which could include Salesforce, Dynamics CRM, and Profisee, is challenging because each system requires a unique identifier for members using its own proprietary format. To solve this problem, sometimes members are simply created on each system to satisfy the ID requirements of each. This is extremely inefficient and increases redundancy.

In SAIM, an attribute for each external system is added in to the entity in Profisee. These attributes have compatible formats with the target systems. For example, to allow data member information to flow between Salesforce, Profisee and Dynamics, you could set up two additional attributes: SA1 and SA2. The attribute SA1 would be configured to hold the values for Salesforce member IDs, and SA2 would be configured to hold the values for Dynamics member IDs. You would next configure an external system list to identify the remote systems.

When using system aware identity management with event processing, all members in the Profisee entity must contain a value for the system aware attribute.

Additional details for the exchange of data are covered in the Eventing section of the help. Map files are required to inform the other systems which of these attributes map to the IDs on those systems, and eventing must be configured to inform Profisee of updates on external systems.

In this way, Profisee can serve as the ultimate authority for member identities on various systems.

The available **system type** values are determined by your subscribers. For example, you can only create a Dynamics CRM system type if you have the corresponding subscribers installed in the server subscribers directory.