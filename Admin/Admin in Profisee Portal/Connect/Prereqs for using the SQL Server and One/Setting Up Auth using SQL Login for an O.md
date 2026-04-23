# Setting Up Authentication using SQL Login for an On-Premise (Non-azure) Database

Profisee users with an On-Premise database must verify that the server allows remote connections and that TCP/IP is enabled before configuring SQL Server for use with Connect. To verify the instance name is correct and that SQL server is configured to allow remote connections:

## 1. Verify the Instance Name

1. Open SQL Server Management Studio (SSMS).
2. In the *Connect to Server* dialog, ensure the **Server name** field contains the correct instance name in the format ServerName\\\\InstanceName.
3. Click **Connect**to ensure you can connect to the SQL Server instance with the provided instance name.

## 2. Check SQL Server Configuration for Remote Connections

1. Open SQL Server Configuration Manager.
2. Expand **SQL Server Network Configuration** and select **Protocols for MSSQLSERVER**.
3. Ensure that **TCP/IP** is enabled. If it is not, right-click on **TCP/IP** and select **Enable**.
4. Double-click on **TCP/IP** to open its properties, then go to the *IP Addresses* tab and ensure:
1. **TCP Dynamic Ports** is blank for all IP addresses.
2. **TCP Port** is set to a specific port number (such as 1433) for all IP addresses.
5. Click **OK** to save the settings.

Note that ports must be configured on the side of the system making the call (e.g. in a SaaS instance, it must be opened on the Profisee side). Depending on the connection policy of the ports, a different port configuration is required.

For Azure SQL Server in **Proxy** connection mode OR a non-Azure SQL server: only port 1433 outbound is required.
For Azure SQL Server in **Default** or **Redirect** modes: port 1433 and ports from 11000 to 11999 outbound are required.

## 3. Configure Windows Firewall

1. Open Windows Firewall with Advanced Security.
2. Click **Inbound Rules** and then **New Rule**.
3. Select **Port** and click **Next**.
4. Choose **TCP** and specify the port number (e.g., 1433) in the **Specific local ports** field. Click **Next**.
5. Allow the connection and click **Next**.
6. Select the network profiles to which the rule applies (Domain, Private, Public) and click **Next**.
7. Provide a name for the rule (e.g., "Allow SQL Server TCP Port 1433") and click **Finish**.

## 4. Restart SQL Server

1. Open SQL Server Configuration Manager.
2. Select **SQL Server Services**.
3. Right-click the SQL Server instance and select **Restart** to apply the changes.

## Finish

Once you have completed these steps, you have verified the instance name is correct and the SQL Server configuration allows remote connections. You may now continue to the next step, [Set Up SQL Login to Assign to Connect to Browse the Server](https://support.profisee.com/wikis/profiseeplatform/set-up-sql-login-to-assign-to-connect-to-browse-the-server).