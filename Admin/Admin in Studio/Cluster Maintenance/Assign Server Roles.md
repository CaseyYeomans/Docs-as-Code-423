# Assign Server Roles

Clustering provides a way to dedicate servers to one or more resource-intensive tasks (such as matching or address verification), and to facilitate event processing. Clustering is a useful way to offload long-running tasks, while freeing up the resources of the primary server to perform other work.

A Profisee cluster consists of at least one primary Profisee Server and zero or more servers running Profisee server. To build a Profisee cluster, you must first install and configure a Web services-enabled Profisee Server. This server includes the IIS Profisee Web application, the IIS Profisee Web Portal application, and the Profisee service. It must be installed on the same server with IIS. Additional instances of Profisee can be installed on various servers within the cluster. Refer to your license for any restrictions.

A Profisee server or service instance may have one or more of the following roles:

- **Web application**

Processes requests made to Profisee, such as queries, through Web services.
- **Job processing**

Processes address verification, matching and survivorship strategies, and stateful requests made to SQL Server, such as requests for matching information.

When a matching strategy is assigned to a server, all the interactive API requests (like VPM for example) are also routed to that server.
- **Background Task Processing**

Triggers audit and eventing processes.
- **Event consuming**

For event processing to function, the cluster must contain at least one sever with the event consuming role. This server is responsible for processing event subscribers.
- **Notification**

The server with the Notification role sends alerts to users when they have tasks requiring attention. The notification server role is required. Error messages for workflows are logged to the event log on the Notification server.

All servers in a cluster share the same SQL Server database and must be located on the same network subnet.

To assign the Notification or Background Task Processor role to a different node, select the role on the node you want to add the role to. You will be prompted to demote the server that originally had the role and move the role to the newly selected node.

If a node with a required role is removed from the cluster, the role from that node automatically is assigned to the primary server.