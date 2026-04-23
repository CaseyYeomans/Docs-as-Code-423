# Transfer Data Within the Same Profisee Cluster

When performing Profisee-to-Profisee transfers within the same cluster, there are several restrictions:

- The source and target in the data transfer strategy must use the same Profisee server connection. If there are multiple Web application servers in the cluster, select one server to use in the connection and always use that connection.
- Using a data transfer strategy to transfer data between different servers that share the same database is unsupported.
- If the subscriber is installed on a Web application server, you must use that server as your Profisee connection.
- The subscriber can be installed on a different server if that server is a processing server.