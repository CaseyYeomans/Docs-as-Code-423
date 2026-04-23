# Planning Your Database Configuration

The Profisee Platform requires an RDS instance of the Microsoft SQL Server engine for operation and storage of data. A new database instance must be created before the EKS cluster is deployed. There are 3 basic considerations and information you will need to provision your database:

1. In what region do you want your RDS database located do you want a specific availability zone?
2. What database engine and instance class are appropriate for your storage, workload, and high-availability requirements?
3. What database instance name and administrative (aka master) username and password do you want to assign for this instance?

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i34f031c1485e9006.png)

### Determining Database Engine, Class, and Public Accessibility Requirements

The most important consideration for the database is its storage, workload, and high-availability requirements. These considerations will affect the choice of engine, class, and availability zone selection. The choice of high availability (or lack thereof) drives your selection of the Microsoft SQL Server Edition you select. If you need high availability, you should refer to the guidance in [High availability (Multi-AZ) for Amazon RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.MultiAZ.html) and [Multi-AZ deployments for Microsoft SQL Server](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_SQLServerMultiAZ.html) when establishing your edition, class, and availability zone configuration.

With respect to storage and workload requirements, you should consider the following:

- Is the Profisee and database instance to be used for Production or Development (Test) purposes?
- How many records across all MDM entities (i.e. tables) do you anticipate for this instance?
- How frequently will this data change and how long will you need to retain history for these tables?
**NOTE**: These considerations affect the volume of the history. Substantial history requirements can place a heavier burden on the searchability of the underlying tables and the data transaction processing load.
- How many concurrent users and system consumers are you likely to be serving?
- Will the server be processing heavy matching loads of substantial volume?

Minimal requirements for a Profisee Database server include:

- 8 cores
- 8 GB RAM

Recommended specifications for your database server are subject to the considerations specified above. Additional scaling and workload guidance can be found in the ***System Requirements for Profisee Server*** section of the [Profisee Platform Installation Guide](https://profisee.magentrixcloud.com/wikis/2021_r2_support/system_requirements_for_profisee_server) on the [Profisee Customer Portal](https://profisee.magentrixcloud.com/aspx/CustomerHome).

If you are a prospect considering Profisee and do not yet have a login to the Profisee Customer Portal, work with your account executive to obtain a PDF copy of this document for your consideration and planning purposes.

A final consideration is whether you want this RDS database to be accessible outside of the [AWS Virtual Private Cloud's (VPC)](https://aws.amazon.com/vpc/?vpc-blogs.sort-by=item.additionalFields.createdDate&vpc-blogs.sort-order=desc) resources? In other words, should any users or external systems have access to the database directly (e.g. SQL Server Management Studio (SSMS), ETL tools, etc.). If so, you should ensure that the **Public access** setting in the **Connectivity** section of the RDS provisioning properties is set to **Yes**. If set to **No,** users/systems outside the VPC will be unable to access the database.

### Determining Your ASW Region & Availability Zone

You may need or want to specify the Availability Zone (AZ) for your RDS database during the provisioning process. The AZ is a function of the AWS Region to in which you are provisioning your database. For performance purposes, it is advisable that your Region selection be the same region in which you configure and provision your EKS cluster to minimize latency between your web and application servers and the database they use during operation.

High availability instances (aka Multi-AZ) do not allow for selection of availability zones. These zones are selected by AWS by default and are associated with the region to which the instance is deployed. For Single-AZ deployments, you do not have to select an AZ. If you do not specify and AZ, a default selection will be made for you during the provisioning process.

For further region and availability zone guidance, refer to [Regions, Availability Zones, and Local Zones](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.RegionsAndAvailabilityZones.html).

### Defining Your RDS Database Instance Name & Master User

When you create your RDS database, you must give the RDS database a unique instance name within the scope of your AWS account, in addition, you will need to provide the master username and password that has administrative privileges to the database.

The following 4 items need to be specified in the **Settings.yaml** file that is used during your cluster deployment:

1. The **Endpoint** URL of the provisioned RDS database. This can be found on the **Connectivity & security** page of the provisioned database.
2. The **DB identifier** (aka database name) of the provisioned instance. This is the friendly name given to the database in the DB cluster identifier field of the **RDS Create Database** wizard page in AWS.
3. The **Master username** which will be used to construct the connection strings used by the various Profisee services when provisioning the cluster and starting the container instances that run the Profisee software.
4. The **Master password** which is used to authenticate users and Profisee system processes that connect to the database during cluster operation.

These are mapped to the following subsection of the Settings.yaml file.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ieb3a4448b6d7aab5.png)