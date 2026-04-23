# MMU User Guide

This guide is intended for administrators moving from Microsoft SQL Server Master Data Services (MDS) to Profisee. Please read all requirements and steps before beginning the migration.

**NOTE:** The MMU is compatible with Profisee Platform v7.1.1 and later.

For information on the use and administration of the Profisee Platform, please refer to the online Help in Profisee FastApps Studio.

For information on compatibility and additional system requirements for a specific version of Profisee, please refer to the Release Notes and Compatibility Matrix for that release.

# Overview

This utility is used to transfer data and model structures from MDS 2014, 2016, and 2017 to Profisee. The utility will create the entities, attributes, relationships, and hierarchies to replace the MDS model.

# Pre-Migration

### Considerations

**Migration is assumed to be a once-only process for each model**. Only one version of a model and its data can be migrated from MDS into Profisee.

**Not all Attribute and Hierarchy types are supported in this release**. The following model configuration artifacts are **not** supported by the migration:

- **File Attributes Collections**
- **Select Hierarchy Scenario**

- Many-to-many (MDS 2016 and later only)
- Multiple levels of recursion
- Recursion that is not at the top of the hierarchy

**If an administrator runs the MMU with Profisee server licensing that limits attributes and records, the attribute and record usage is calculated in advance of the migration**. The following information is logged to the console when a licensing limit error is detected. The red text indicates how many attributes and entities would be created from the selected model and version:

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i933384c6b3878bdf.png)

Record usage in the MDS source system is based on a count of consolidated and leaf members for the selected version. Explicit hierarchies are structured differently in Profisee, and File attributes are not included in the count, so the number of attributes counted in Profisee will differ from that of MDS.

During migration, entity names are restricted to 50 characters. **However,**entities used to relationships within hierarchies require additional characters, which may cause errors in entities with long names.

To avoid these issues, ensure these entity names are no more than 42 characters in length.

### Required Permissions

The following permissions are required to oversee the migration process:

**MDS 2014** - Read Permissions on the model **MDS 2016/2017** - Read Permissions on the model **Profisee** - Super Admin

### Download the Utility

The utility is lightweight and easy to use, with no installation required. To download it from the Profisee website:

1. Navigate to The [Profisee Support Portal](https://support.profisee.com/aspx/ProfiseeCustomerHome) > Downloads > Resources > [MDS Migration Utility](https://support.profisee.com/sys/folder/detail/7Os00000000002d00aM?retUrl=%2Fsys%2Fdocument)
2. Click the item to download the zip file.
3. Unzip the file into the desired directory.

# Launch the Utility

From the MDS Migration Tool folder, double-click **MDSMigration.exe**.![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i5fefb604b77608f6.png)

The MDS Migration window opens.

# Migration Process

To migrate your MDS database to Profisee:

1. Enter the URL for the location of your Profisee instance. Refer to the Profisee Platform install guide for the format of the URL.![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i322a2d02533ce93d.png)
2. Enter the URL for the location of your MDS database.![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i335b0d5c6c7e6e11.png)
3. Select the desired MDS model from the drop-down menu.![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-ia4ae8a7960b48c6c.png)
4. Select the desired data version. Remember that you can only migrate one version of a model from MDS into Profisee.![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i880cf3a62c906eef.png)
5. Click **Start**.![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-ia2ce6481722461d6.png)If you try to migrate the model when your license limit is exceeded, the **Start** button is disabled. Correct the license issue and restart the utility to continue. Refer to Considerations for details.

Note that **Date** attributes which include the "Show time" property in Maestro will be created and transferred as **Date** values, not **Date Time** values.

### Entity and Hierarchy Name Length Limit

There is a 50-character limit for a final entity or hierarchy name in the target. If the limit is exceeded, the prompt below appears. Enter a modified name of less than 50 characters in the free-text field.

This name must be unique among all of the names that will be published to the Profisee server inclusive of any entity names that may already exist in the Profisee data model.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-ied3262f935746163.png)

If you do not want to rename an entity, select **Skip**. Note that if you skip the rename, the entity will not be created and any hierarchies related to that entity are not created. In addition, any domain-based attributes that relate to this entity are also skipped.

Profisee allows reduced precision for number attributes than what is provided in MDS. Warnings will be returned if precision is reduced, but most data will transfer successfully.

For example: a number with 12 decimals in MDS will be created as a number with 8 decimal places in Profisee. Values will be rounded appropriately. If a number value is so large that it will overrun the allowed precision then no values will be transferred in this entity. This can be avoided by temporarily deleting these values in MDS so all other values transfer.

For example: an MDS Number that holds 11 decimal places (decimal (27,11) would allow 16 numbers before the decimal and 11 decimal values. If you have a value that large, (total 27 digits) that would not transfer to decimal (26,8) causing all members in the entity to fail.

# Post-Migration

### Entity Creation in Profisee

Leaf entities are created as ModelName\_EntityName. Explicit hierarchy entities storing consolidated members are created as ModelName\_EntityName\_ExplicitHierarchyName. If a consolidated entity is renamed, the migrated hierarchy will use the same name.

### Explicit Hierarchy Migration

Explicit hierarchy relationships are replaced by a new entity with a recursive DBA containing the consolidated members.

The leaf entity contains a DBA column for the new explicit domain entity.

Relationships are created during migration along with the new hierarchy, with the recursive relationship and the new parent child relationship, from the leaf to the new explicit entity.

### Derived Hierarchy Migration

Supported derived hierarchies are migrated. Unsupported derived hierarchies are skipped and a warning is written to the console output.

**Tracking Progress & Errors**

The console window, shown below, provides a running log of events as the migration proceeds. The log includes errors and warnings, including the specific entities and attributes affected.

When the migration is complete, the Copy function becomes available, allowing you to save the log as a text file for future reference.

Errors and warnings are also written to the Windows Application event log.![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i55511c48c6578b4d.jpg)