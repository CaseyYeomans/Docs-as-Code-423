# Add a New Profisee Connection

If you have multiple Profisee Server application instances, you can set up multiple named connections to allow your Profisee FastApp Studio to connect with each of them.

1. Click **Connect** on the main toolbar.
2. Do one of the following:

**--or--**

- Click the **Connection** list, and then click **Create New** on the menu.
- Click **Manage your list of named connections**, and then click **Add**.
3. Enter a name for the new connection in the **Name** field.
4. Enter the connection string to the Profisee service in the **URL** field.

The connection string follows this general format to connect using Web services on a Profisee Web application server:

http://serverName/profiseeWebApplication/service.svc

**--or--**

net.tcp:// serverName/profiseeWebApplication/service.svc

If no port is included, even when using the net.tcp protocol, then Profisee will connect using Web services rather than the Profisee Windows service.

**--or--**

https://serverName/profiseeWebApplication/

The following connection string format is obsolete and should no longer be used: *net.tcp://serverName:portNumber/ProfiseeWebApplication*

5. Click **Test** to make sure that you have entered your connection information correctly.
6. Click **Save**.
7. Select the new connection from the **Connection** menu and then click **Connect**. You can use this connection by default by selecting **Connect when Profisee starts**.

You can configure Profisee FastApp Studio to connect to Profisee Server using either the net.tcp or http protocol. For better performance on internal networks, net.tcp is recommended. However, for environments with restrictive firewalls or other limitations, the http protocol is available.