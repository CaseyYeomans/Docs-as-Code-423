# Change Roles in a Cluster

## Changing A Notifications or Background Task Processor Server

Use this procedure when you want to change the server with the Notifications or Event publishing role to a different server in your cluster when the roles are already assigned.

1. [Assign](https://support.profisee.com/wikis/profiseeplatform/assign_server_roles) the role on the server you want to promote.
2. When you are prompted to do so, select to demote the server that originally had that role.

The new server is promoted, and the original server no longer has the role.

## Changing An Event Consuming Server With Single-Server Configuration

Use this procedure when you have one server with the Event consuming role in your cluster, and you want to assign that role to another server.

1. [Assign](https://support.profisee.com/wikis/profiseeplatform/assign_server_roles) the role to the server you want to promote.
2. [Register](https://support.profisee.com/wikis/profiseeplatform/register_a_subscriber) subscribers on the new event consumer.
3. Remove the Event consuming role from the original server.

The new server now has the Event consuming role.