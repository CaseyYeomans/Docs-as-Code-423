# Remove a Server Instance from a Cluster

Removing a Server Instance:

1. On the server you want to remove, launch Configuration Manager.
2. Click **Edit an existing instance**.
3. If there is more than one instance installed on the machine, select the instance to remove in the list.
4. Click **Remove this instance**.

Confirm the removal.
5. Click **OK** when the removal is complete.

## Restrictions on Removing a Server Instance

### Event Publishing Servers

Every cluster must have one server with the event publishing role. To remove an eventing publishing server instance, you must first assign a new event publishing server. This demotes the original server and removes the event publishing role from it. After the server has been demoted, it can be removed.

### Event Consuming Servers

To remove an event consuming server from a cluster, you must first remove all subscriptions, subscriber configurations, and subscribers from it.

### Processing Servers

Processing servers that are not restricted because they are event publishing or event consuming servers can be removed at any time, including while the server is processing a strategy. Any strategies that are currently being processed will end with errors. Any strategies configured for a processing server that is removed from the cluster will default to the Web application server where they are launched.

Although it is possible to remove a processing node while processing is ongoing, it is not recommended. Best practice is to ensure the system is idle when removing a node from a cluster.

### Web Application Servers

Like processing servers, Web application server instances can be removed at any time as long as they are not restricted by publishing or consuming server roles. One exception is the primary Web server--the first Profisee Web server installed in a cluster. All other servers in the cluster must first be removed before the primary server can be removed.

If the web application server being removed is part of a high-availability cluster, additional configuration may need to be adjusted with respect to any load balancer in use on the cluster.