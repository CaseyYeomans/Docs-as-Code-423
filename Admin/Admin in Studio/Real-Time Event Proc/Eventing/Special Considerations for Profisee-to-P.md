# Special Considerations for Profisee-to-Profisee  Data Transfers

In most cases, Profisee-to-Profisee transfers will occur between Profisee servers in different clusters. However, it is possible to transfer data within the same Profisee server (or between Profisee servers in the same cluster), possibly for testing purposes.

When Profisee servers in two different clusters are involved, both source and target servers must be licensed for the Profisee (R) Integrator (formerly Federation Manager) feature. Integrator provides connection security and allows only the configured account to write to the target system.

It is not necessary to have servers with the event consuming and publishing roles, or subscribers located in the cluster where the target Profisee server is located. The target server in these circumstances can only receive data from the source server.

In the case of bidirectional transfers between clusters, each Profisee server becomes both the target and the source server. Both clusters must have complete event processing configurations (event consumers, event publishers, subscribers, Data Transfer Controllers). These requirements are in addition to the Integrator licensing requirement, which is necessary for unidirectional transfers between Profisee servers.

External events are never used with Profisee-to-Profisee data transfers. A Profisee server always initiates the transfer, so only Profisee events are involved in the process.

If the Profisee connection in the data transfer strategy differs from the current server, then the current server will be used as the connection instead. For more information, see [Overriding Connections in Integrator Strategies](https://support.profisee.com/wikis/profiseeplatform/override_connections_in_integrator_strategies).