# Planning Your SQL Server Configuration

When considering your SQL Server configuration for the Profisee AKS ARM deployment, you have two options:

- Provision a new Azure SQL Database automatically associated with this Profisee cluster, or
- Allow the Profisee cluster to provision its database in an existing SQL Server instance. This instance can be:
- A pre-created *empty* Azure SQL Database
- An Azure SQL Managed Instance
- A SQL Server instance on an IaaS VM in Azure or other cloud platform
- An on-premise SQL Service instance in your office or data center

The process flow below highlights this critical decision point and then shows the actions you should take during planning to ensure that the deployment process can successfully deploy the Profisee Platform's database when the ARM template process is executed.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iccd3d346bd9c8184.png)

In the process diagram above, there exists a single decision point: do you want to automatically provision a new Azure SQL Database associated with this Profisee cluster? This answer - Yes or No - is specified in the **SQL Server Create New** property of the ARM template.

**If you choose 'Yes,' you must:**

- Define and record a globally unique SQL Server name that will be used to reference this SQL instance from anywhere in your network. Record this name as you will need to specify this name in the **SQL Server Name** property of the ARM template.
- Define the SQL Server administrator user name and password that will be used by the ARM deployment process to access this server during the deployment process. Record these names as you will need to specify them in the **SQL Server User** and **SQL Server Password** properties of the ARM template.
- Define the Profisee database name that will be used by the platform to store all of your platform artifacts and data. If using a name other than the default - **Profisee** - then you should record this name as it will be needed to specify the **SQL Server Database Name** property of the ARM template.

**If you choose 'No,' you must:**

- Obtain an existing SQL Server Name and administrative credentials of the SQL Server instance that you want to contain the cluster's Profisee database. Record the SQL Server name and administrative credentials because you will need them to specify the **SQL Server Name**, **SQL Server User**, and **SQL Server Password** properties of the ARM template.
- Define the Profisee database name that will be used by the platform to store all of your platform artifacts and data. If using a name other than the default - **Profisee** - then you should record this name as it will be needed to specify the **SQL Server Database Name** property of the ARM template.
- Open the firewall on the target SQL Server machine to the outbound IP address of the Profisee cluster.

The firewall on your SQL Server instance cannot be configured until the Profisee cluster is provisioned. This introduces a chicken-and-egg paradox; the cluster cannot provision its database until the firewall is opened but the firewall cannot be opened until you know the outbound IP address of the cluster. Fortunately, there is a window of time where this can be performed. See [Configuring the Firewall on SQL Server for Your Profisee Cluster](https://support.profisee.com/wikis/profiseeplatform/configuring_the_firewall_on_sql_server_for_your_profisee_cluster) for details on when and how to open up the firewall to the Profisee cluster.

As part of this planning process, you should have identified the following properties of the Profisee ARM template:

- SQL Server Create New
- SQL Server Name
- SQL Server User
- SQL Server Password
- SQL Server Database Name

You may now continue to [Planning Your File Storage Configuration](https://support.profisee.com/wikis/profiseeplatform/planning_your_file_storage_configuration), or return to [Planning Your Deployment](https://support.profisee.com/wikis/profiseeplatform/deploying_profisee_using_the_arm_template).

### See more

- [Planning Your Deployment](https://support.profisee.com/wikis/profiseeplatform/deploying_profisee_using_the_arm_template)
- [Deploying the AKS Cluster using the ARM Template](https://support.profisee.com/wikis/profiseeplatform/deploying_the_AKS_cluster_with_the_arm_template)
- [Configuring the Firewall on SQL Server for Your Profisee Cluster](https://support.profisee.com/wikis/profiseeplatform/configuring_the_firewall_on_sql_server_for_your_profisee_cluster)