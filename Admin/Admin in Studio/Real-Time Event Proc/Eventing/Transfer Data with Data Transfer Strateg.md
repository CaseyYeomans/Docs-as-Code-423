# Transfer Data with Data Transfer Strategies

Data transfer strategies can be used in two ways:

- For bulk transfers, using Integrator (formerly Federation Manager)
- To synchronize two systems, using Profisee event processing

To perform initial system loads, use the Integrator application, or process a data transfer strategy using the Federation Transfer command line option. Data transfer strategies in Integrator will transfer all mapped data values from one system to another, restricted only by filtering options.

To keep the two systems synchronized after the initial load, you can use the same data transfer strategy, but with Profisee event scenario settings around it. Instead of transferring all data, event processing only transfers information about members that change.

Consider the situation where you have two systems: Dynamics CRM and Profisee. The data transfer strategy maps a Profisee Customer entity to a Dynamics CRM Contacts entity, so that the following attributes are mapped:

| These Profisee attributes: | Are mapped to these Dynamics CRM attributes: |
| --- | --- |
| Name | Full Name |
| Address Line 1 | Address |
| EmailAddress | Email |

In the data transfer strategy, Profisee is the source connection, and Dynamics CRM is the target connection.

When processed in Integrator, all of the members from Profisee will transfer to Dynamics CRM. The attribute values included in the transfer will be Name, Address Line 1, and EmailAddress. The values will transfer to the mapped attributes on the Dynamics CRM system.

Data on Profisee :

| Name | Address Line 1 | EmailAddress | State | Marital Status |
| --- | --- | --- | --- | --- |
| Steve Jones | 1 Main | stevejones@exampledomain3.com | VT | M |
| Mary Smith | 101 Maple | marysmith@exampledomain2.com | TX | S |
| John Brown | 202 Oak | johnbrown@exampledomain1.com | ME | D |
| Liz Green | 5 Alder | lizgreen@exmapledomain4.com | FL | S |

Data on Dynamics CRM after initial load from Profisee :

| Full Name | Address | Email |
| --- | --- | --- |
| Steve Jones | 1 Main | stevejones@exampledomain3.com |
| Mary Smith | 101 Maple | marysmith@exampledomain2.com |
| John Brown | 202 Oak | johnbrown@exampledomain1.com |
| Liz Green | 5 Alder | lizgreen@exmapledomain4.com |

When the same data transfer strategy is included in event processing, however, it is the triggering action in the event scenario that defines when data transfers. Profisee event scenarios define the events that cause data to move between systems.The edited member defines the data that transfers, and the mapped attributes limit the attribute values that transfer.

For the purposes of this example, the triggering action is Update, and the Attributes tab of the scenario includes All Attributes in the entity. So, any change in a member triggers a transfer of that member to Dynamics CRM.

For example, this change in Profisee :

| Name | Address Line 1 | EmailAddress | State | Marital Status |
| --- | --- | --- | --- | --- |
| Steve Jones | 1 High Street | stevejones@exampledomain3.com | VT | M |

causes the Steve Jones member to transfer to Dynamics CRM, resulting in this data on the Dynamics CRM system:

| Full Name | Address | Email |
| --- | --- | --- |
| Steve Jones | 1 High Street | stevejones@exampledomain3.com |
| Mary Smith | 101 Maple | marysmith@exampledomain2.com |
| John Brown | 202 Oak | johnbrown@exampledomain1.com |
| Liz Green | 5 Alder | lizgreen@exmapledomain4.com |

Only the single member would transfer, however. This is the key difference between event processing and processing strategies within Integrator.

Because the event scenario is monitoring all attributes, transfers can occur that result in no data changes on the target system.

For example, this change on Profisee :

| Name | Address Line 1 | EmailAddress | State | Marital Status |
| --- | --- | --- | --- | --- |
| Mary Smith | 101 Maple | marysmith@exampledomain2.com | TX | M |

causes the Mary Smith member to transfer to Dynamics CRM, resulting in this data on the Dynamics CRM system:

| Full Name | Address | Email |
| --- | --- | --- |
| Steve Jones | 1 Main | stevejones@exampledomain3.com |
| Mary Smith | 101 Maple | marysmith@exampledomain2.com |
| John Brown | 202 Oak | johnbrown@exampledomain1.com |
| Liz Green | 5 Alder | lizgreen@exmapledomain4.com |

The data values are the same, because the Marital Status attribute was not mapped to an attribute in Dynamics. But because the scenario monitors all attributes in the entity, any change triggers a transfer for the changed member, even in attributes that are not mapped in a data transfer strategy.

When the triggering action is Create, the behavior is similar. Only the created member is transferred, according to the data transfer strategy settings.