# Install Additional Web Application Servers

##

## Web Application Server Overview

After a cluster is established with a primary Profisee server node, you can install additional nodes up to the number indicated by your license.

To install a Web application server in an existing cluster:

1. On the server where you are performing the installation, make sure the firewall allows communication using the Profisee service port configured for the primary server connection (default port is 8003).
2. Copy the server installation files to the physical node where you are installing the new server.
3. Install the Profisee software using the **Profisee.msi** file.
4. Accept the End-User License Agreement, and then complete the server installation.
5. Either select to run Configuration Manager immediately after installation completes, or launch Configuration Manager manually from the Windows Start menu in this location:

`Programs > Profisee Server > Profisee Server Configuration Manager`
6. On the first Configuration Manager dialog, click **Add to a cluster**.
7. In the Profisee Web URL field, type the Client ID and connection string for the primary server.
8. Click **Next**.

The license information displays.
9. Click **Next**.

The Windows Service information displays.
10. In the **Password** field, enter the password for the Profisee service account.

The service account information was added when the primary server was installed. This information must be the same for the processing server.

11. Click **Test Permissions** to verify the credentials.
12. Click **Next**.

The Web Application configuration dialog displays.
13. Select the virtual directory from the **Virtual directory** list.
14. Under Profisee Web application, the Profisee virtual directory is already selected and is read-only.
15. Configure the Profisee Web application pool.

Do one of the following:

**--or --**

- Click the down arrow to open the **App Pool** list and select an existing application pool.
1. Click **Create new app pool** to create a new application pool.

The Application Pool dialog appears.
2. In the **App Pool Name** field, type a name for the new application pool.

Example: "Profisee"
3. In the **User Account** field, type the user name to use for the application pool.

The application pool account:

- Must be a domain account
- Must be the same between all web-enabled nodes in the cluster
- Should have a password that does not expire (to reduce maintenance)
- Will be assigned to the role that connects to Profisee
4. In the **Password** field, enter the password for the user account.

Enter it again in the **Confirm Password** box.
5. Click **Save**.
16. The Profisee Portal application virtual directory is already selected for you.
17. Under Profisee Portal application, select the desired application pool from the App pool list.

Do one of the following:

**--or --**

- Click the down arrow to open the list and select an existing application pool from the **App Pool** list.
1. Click **Create new app pool** to create a new application pool.

The Application Pool dialog appears.
2. In the **App Pool Name** field, type a name for the new application pool.

Example: "Profisee"

Create separate application pools for the web application and the web portal application.

19. If this server is to be used only for fail over conditions, select "This server is for standby use only within the cluster".

If this server is going to be used in a high-availability cluster, do not check this box. Refer to High-Availability Clusters in the Profisee Platform Installation Guide for details.

This option does not appear unless your license supports the standby option.

1. In the **User Account** field, type the user name to use for the application pool.

The application pool account:

- Must be a domain account
- Must be the same between all web-enabled nodes in the cluster
- Should have a password that does not expire (to reduce maintenance)
- Will be assigned to the role that connects to Profisee.
2. In the **Password** field, enter the password for the user account.

Enter it again in the **Confirm Password** box.
3. Click **Save**.

20. Click **Next**.

The **Summary** dialog appears.

21. Verify your changes in the Summary dialog.
22. Click **Back** to go back to any previous sections to make changes, or click **Next** to finish configuring the Profisee Server components.

The **Progress and Finish** dialog appears.
23. When the configuration completes, click **Finish**, and then click **Exit**.