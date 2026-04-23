# Configuring the Firewall on SQL Server for Your Profisee Cluster

If you have opted to use an existing SQL Server instance with your Profisee cluster, you must ensure the SQL Server machine has its firewall open to allow inbound traffic from the outbound address of the cluster. This can be done in one of two ways:

- You can open the firewall to all Azure services.

or

- You can open the firewall to only the outbound IP address of the Profisee cluster.

Option 1 is easier, but is potentially less secure because the database server is open to traffic from all services in your subscription. Option 2 provides more security, but requires you to determine the outbound IP address of the cluster.

Regardless of which option you choose, the firewall must be configured and opened within a specific timeframe to successfully deploy your Profisee instance. For more information, see **Timeframe for Configuring the Firewall** at the bottom of this page.

Note that if you select **Yes** for the **SQL Server Create New** property of the ARM template, the SQL Server firewall is configured automatically and the steps below are not required.

## Option 1

To open the firewall in the Azure portal to all services for an Azure-hosted SQL Server:

1. Navigate to the SQL Server resource used for deployment. You can find this within your Resource Group in the [Azure portal](https://portal.azure.com/#home).
2. Click **Show firewall settings** in the **Essentials** panel at the top of the page.
3. Select **Yes** for **Allow Azure services and resources to access this server**.

## Option 2

To restrict the access to only the Profisee cluster:

1. Navigate to the SQL Server resource. You can find this within your Resource Group in the [Azure portal](http:/profiseeplatform/portal.azure.com/#home).
2. Click **Show firewall settings** in the **Essentials** panel at the top of the page.
3. Select **No** for **Allow Azure services and resources to access this server**.
4. Add a new firewall rule for the SQL server by specifying a **Rule name**, **Start IP**, and **End IP**. The **Rule name** can be titled as desired. The **Start IP** and **End IP** must match the outbound address of the Profisee cluster. See **Locating the Outbound IP Address of Your Cluster** below for details on finding this address.

### Locating the Outbound IP Address of Your Cluster

To find the outbound address of the cluster in the Azure portal:

1. Navigate to the resource group associated with the cluster.
2. Select the Cluster resource (type is **Kubernetes service**).
3. Click the **Properties** blade in the left-hand navigation column under **Settings** to view the properties of the Kubernetes cluster resource.
4. Click the **Infrastructure resource group** on the properties page.
5. Locate the **Public IP address** for the outbound address of the cluster. This has a **Name** property that does not begin with the word 'kubernetes'. The 'kubernetes' IP address is the inbound address of the cluster. It is typically represented as a GUID.
6. Click the **Name** property of the outbound **Public IP address** to obtain the address. The address is shown in the **IP address** field of the resource properties.

## Timeframe for Configuring the Firewall

There is a chicken-and-egg paradox that must be dealt with when setting up your firewall for access by the cluster. The paradox is this: You cannot specify the outbound address of the cluster until it is provisioned, but when it is provisioned, the Profisee instance will require access to the SQL Server to start properly. Fortunately, there is a window of time whereby you can determine the outbound address of the cluster before the cluster attempts to access the SQL Server instance. You can use this window to open the firewall. The diagram below illustrates the timing of this process.

| | |
| --- | --- |
| The Deployment Team starts the process by filling out the ARM template as usual. The ARM template must specify the FQDN of the existing SQL server instance on which the firewall must be opened. | |
| Once the ARM template has been submitted, the Deployment Team must wait for the cluster resources to be provisioned by the Profisee deployment process. The team can monitor the deployment process via the Azure portal by clicking the "Deployment in progress..." notification within the notifications tab. This navigates to the Deployment Progress page. |
| On this page, you can see the deployment steps process in real time. After the step **InstallProfiseePlatform** succeeds, there exists a roughly 10 minute window where the cluster has been provisioned, and thus the outbound address of the cluster can be determined but before the Profisee nodes within the cluster begin to communicate with the database server. The Deployment Team should use this window to determine the outbound IP address and open the firewall. |
| Once the cluster nodes have configured themselves and started users on the Deployment Team can log in to the Profisee instance and validate the deployment. |

If the Deployment Team misses the window and the firewall is not open, the Profisee nodes will fail to start because they will not be able to access the database server. However, it is possible to finish the process of configuring the firewall and to restart the instance configuration process without re-provisioning the entire cluster. For more details, see [Reconfiguring the Instance without Re-executing the ARM Template](https://support.profisee.com/wikis/profiseeplatform/restart_the_instance_configuration_process_without_re-executing_the_arm_template).

### See more

- [Planning your SQL Server Configuration](https://support.profisee.com/wikis/profiseeplatform/planning_your_sql_server_configuration)
- [Reconfiguring the Instance Without Re-executing the ARM Template](https://support.profisee.com/wikis/profiseeplatform/restart_the_instance_configuration_process_without_re-executing_the_arm_template)