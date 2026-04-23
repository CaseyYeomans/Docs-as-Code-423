# Planning Your File Storage Configuration

Each Profisee cluster must have access to central file storage resource where files are stored for the following functions:

- Certificates that are used by the various containers in the cluster to support secure communications over HTTPS
- Default and custom subscribers that plug in to Profisee's Real-time Event Processing subsystem
- Workflows that are published to the cluster
- Unstructured file attachments that are related to master data within your model

When planning your Profisee cluster configuration, you will need to ensure file storage exists or is provisioned during the cluster deployment. The amount of storage you need is largely defined by whether you plan to use the File Attachments feature of the platform. File storage needs for the platform are negligible unless you plan to attach unstructured data (files) to your master data records. If you plan to attaches files to your master records, the type and amount of storage become more important considerations.

The following diagram illustrates the decision process related to file storage.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i6d1668733146f661.png)

The critical decision in this process is whether you want storage to be automatically provisioned as part of the deployment process. This is determined by the **Storage Account Create New** property of the ARM template.

**If you answer 'Yes,' you must:**

- Determine the needs of your storage. In this process, you are determining the Azure Storage [SKU Type](https://docs.microsoft.com/en-us/rest/api/storagerp/srp_sku_types) which is ultimately specified in the **Storage Account Type** property of the ARM template. The ARM template offers the following choices for the SKU Type:
- **Standard\_LRS**
- **Standard\_ZRS**
- **Standard\_GRS**
- **Standard\_RAGRS**
- **Premium\_LRS**

The SKUs effectively define a combination of [performance tiers](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-overview?toc=/azure/storage/blobs/toc.json#performance-tiers) (Standard vs. Premium) and [redundancy](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-overview?toc=/azure/storage/blobs/toc.json#redundancy) (LRS, ZRS, GRS, etc.). For more details, refer to the [Storage account overview](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-overview?toc=/azure/storage/blobs/toc.json#performance-tiers) topic in Microsoft's Azure documentation. The **Standard\_LRS** SKU is generally sufficient if you do not plan to use File Attachments. If you plan to use the File Attachments feature heavily, then further consideration regarding performance and redundancy may be warranted.

- Define and record a globally unique storage account name for your storage. You will need this when specifying the **Storage Account Name** in the ARM template.
- Define and record the name of the file share within the specified storage account. The ARM template defaults the **Storage Account File Share Name** to the value "files", but this can be changed if desired.

**If you answer 'No', you must:**

- Obtain and record the name of an existing storage account you want to use to store files for your Profisee cluster. This name will be specified as the Storage Account Name in the ARM template when you run the deployment.
- Obtain an Access Key associated with the storage account. This key acts as the credentials that allow access to the storage account during the deployment process. The storage account contains 2 access keys. Both work for the purposes of allowing the ARM deployment process to access the storage account. Record one of the keys for use in the **Storage Account Access Key** property of the ARM template.
- Define and record the name of the file share within the specified storage account. The ARM template defaults this to the value "files" but this can be changed if desired.

As part of this planning process, you should have identified the following properties of the Profisee ARM template:

- Storage Account Create New
- Storage Account Name
- Storage Account Access Key (not required if creating a new storage account)
- Storage Account Type (not required if using an existing storage account)
- Storage Account File Share Name

You may now continue to [Planning your HTTPS Security](https://support.profisee.com/wikis/profiseeplatform/planning_your_https_security), or return to [Planning Your Deployment](https://support.profisee.com/wikis/profiseeplatform/deploying_profisee_using_the_arm_template).

### See more

- [Planning Your Deployment](https://support.profisee.com/wikis/profiseeplatform/deploying_profisee_using_the_arm_template)
- [Deploying the AKS Cluster using the ARM Template](https://support.profisee.com/wikis/profiseeplatform/deploying_the_AKS_cluster_with_the_arm_template)
- [Microsoft Storage Account Overview](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-overview?toc=/azure/storage/blobs/toc.json#naming-storage-accounts)