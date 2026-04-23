# Using the NTFS Service Provider

# NTFS Service Provider

Profisee Administrators can use the **NTFS Service Provider** to connect to file systems using NTFS (New Technology File System) for importing and exporting Parquet files. This allows you to read data from and write data to files stored on local or network file systems.

## Creating an NTFS Service Configuration

Before you can create strategies to import or export data, you must first create an NTFS service configuration.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-icc3ac7f87c0b4361.png)

### Step 1: Access Service Configurations

1. Navigate to the Administration section of Profisee.
2. Under the **Connect** tab, click on **Service Configurations**.
3. Click the **+** icon to add a new configuration.

### Step 2: Configure Basic Settings

In the **Add New Configuration** dialog, enter the following information:

* **Configuration Name**: Enter a descriptive name for your configuration (e.g., "NTFS Service Config").
* **Service Provider**: Select **NTFS** from the dropdown list.
* **Base File Path**: Enter the base directory path where files will be accessed (e.g., `C:\files`). This can be expanded later in the strategy.

### Step 3: Configure Authentication

Select an **Authentication Scheme** from the dropdown:

* **Basic**: Standard username and password authentication
* **AD**: Active Directory authentication

Then enter your credentials:

* **Username**: Enter the username for accessing the file system.
* **Password**: Enter the password for the specified username.

### Step 4: Complete Configuration

1. Click **Continue** to create the service configuration.
2. The configuration will be created, and you'll see the **NTFS Service Config** details page.

### Viewing and Editing Configuration

Once created, the NTFS Service Configuration page displays two tabs:

#### Overview Tab

The Overview tab displays read-only information about your configuration:

* **Configuration Name**: The name you assigned to this configuration (editable).
* **Service Provider**: Displays "NTFS".
* **Provider Type**: Displays "File".

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic956f538b39505f8.png)

#### Settings Tab

The Settings tab allows you to view and modify:

**Authentication**:

* **Authentication Scheme**: The selected authentication method (Basic or AD).
* **Username**: The username for file system access.
* **Password**: The password (displayed as "Password" for security).

**Location**:

* **Base File Path**: The root directory for file operations (e.g., `C:\files`). This can be expanded later in the strategy.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iab641bd1359b2a8c.png)

Click **Save** or **Save and Close** to save any changes.

---

## Creating an NTFS Import Strategy

After creating an NTFS service configuration, you can create import strategies to bring Parquet data into Profisee entities. When multiple files are dropped in an external folder that is configured for a connect strategy, those files are picked up and processed in the order they were added (oldest file first).

### Step 1: Create New Strategy

1. Navigate to the **Strategies** window under the **Connect** tab.
2. Click the **+** icon to add a new strategy.
3. The **Add New Integration Strategy** dialog appears.

### Step 2: Configure Strategy Basics

In the dialog, enter the following:

* **Strategy Name**: Enter a descriptive name (e.g., "NTFS Import Strategy").
* **Entity**: Select the target entity where data will be imported (e.g., "ABCCode").
* **Service Configuration**: Select your NTFS service configuration (e.g., "NTFS File SC").
* **Integration Flow**: Select **Import** from the dropdown.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iac66cf17b8c00fa6.png)

Click **Continue** to proceed to strategy configuration.

### Step 3: Configure Strategy Details

The strategy configuration page opens with four tabs: **Overview**, **Import Map**, **Run Options**, and **Scheduling**.

#### Overview Tab

The Overview tab displays the strategy details:

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ica5eb16171fefdc0.png)

**Provider Details** section:

* **Strategy Name**: The name of your strategy.
* **Entity**: The target entity.
* **Provider Type**: Displays "File".
* **Configuration**: Your NTFS service configuration.
* **Integration Flow**: Displays "Import".

**Target Location** section:

* **File Type**: Displays "Parquet".
* **File Path**: Displays the file path based on the base file path in the service configuration.
* **Relative Path**: Enter the path to your Parquet file relative to the Base File Path (e.g., `\mediatag.file.core.windows.net\fileshare`).

#### Import Map Tab

The Import Map tab is where you define how Parquet file columns map to entity attributes.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3306eb80967d7656.png)

The mapping interface displays:

* **[Entity Name] Attribute**: The entity attribute name (e.g., "Name", "Code").
* **Type**: The data type of the attribute (e.g., "Text (250)").
* **Response Property**: The source column from your Parquet file.

To add attributes:

1. Click the **+ (Add)** button to create a new mapping row.
2. The system will display available entity attributes.
3. For each attribute, specify which Parquet file column should be populated in the **Response Property** field.
4. Repeat for all attributes you want to import.

#### Run Options Tab

The Run Options tab controls how the strategy executes.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ie0a9c4933337f139.png)

**Execution** section:

* **Run-as user**: Select the user account under which the strategy will execute.
* **File Naming Pattern**: Specify how files are named (e.g., "ABCCode + UTC Timestamp"). Asterisks and question marks are allowed in the file naming pattern.
* **On-Demand asynchronous execution**: Check this box to enable manual execution with asynchronous processing.
* **File Record Limit**: Enter the maximum number of records to process per file (e.g., 10000). If records beyond this limit are processed, a new file will be created for the remainder.

#### Scheduling Tab

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-if7b5ea95f1aa5d57.png)

The Scheduling tab allows you to run the import on a recurring schedule.

If no schedule is configured, the strategy will only run when manually executed.

### Step 4: Save and Test

1. Click **Save** or **Save and Close** to save your import strategy.
2. To test, execute the strategy manually and verify records are imported into your entity.

---

## Creating an NTFS Export Strategy

Export strategies allow you to write entity data to Parquet files in your file system.

### Step 1: Create New Strategy

1. Navigate to the **Strategies** window under the **Connect** tab.
2. Click the **+** icon to add a new strategy.
3. The **Add New Integration Strategy** dialog appears.

### Step 2: Configure Strategy Basics

In the dialog, enter the following:

* **Strategy Name**: Enter a descriptive name (e.g., "NTFS Import Strategy").
* **Entity**: Select the target entity where data will be imported (e.g., "ABCCode").
* **Service Configuration**: Select your NTFS service configuration (e.g., "NTFS File SC").
* **Integration Flow**: Select **Export** from the dropdown.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iac66cf17b8c00fa6.png)

Click **Continue** to proceed to strategy configuration.

### Step 3: Configure Strategy Details

The strategy configuration page opens with four tabs: **Overview**, **Export Map**, **Run Options**, and **Scheduling**.

#### Overview Tab

The Overview tab is similar to the import strategy, displaying the strategy details and file path information.

#### Export Map Tab

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3a3dc4178a94fa20.png)

The Export Map tab is where you define which entity attributes to include in the exported Parquet file.

This list displays a 1:1 mapping for all attributes contained in the entity. These mappings can be edited or removed, and new attributes can be added with the **plus (+)** icon. Changes made to the Export Map do not impact attributes in Profisee.

#### Run Options Tab

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i6752c8aaa92986b7.png)

The Run Options tab allows you to determine how and when the strategy is triggered. The available options are as follows:

* **Run-as user**:The account used to make changes when the strategy is triggered.
* **File naming Pattern:** The naming format for files.
* **On-Demand asynchronous execution:**Select to enable On-Demand asynchronous execution.
* **File Record Limit**: The maximum number of records to process per file (e.g., 10000). If records beyond this limit are processed, a new file will be created for the remainder.
* **Triggers when records are added:**Causes the strategy to run any time records are added to the entity.
* **Added records filter:**Allows you to create an expression that limits the above option to run only when the records added meet certain criteria.
* **Trigger when records are updated:**Causes the strategy to run any time records in the entity are updated.
* **Updated records filter:**Allows you to create an expression that limits the above option to run only when the records edited meet certain criteria.
* **Trigger when records are deleted:**Causes the strategy to run any time records in the entity are deleted.
* **Delete records filter:**Allows you to create an expression that limits the above option to run only when the records deleted meet certain criteria.

#### Scheduling Tab

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i89db832aab5c5c18.png)

If you want to execute the strategy on a schedule, create a schedule by adding a name, Cron expression, and expression to the options under the Scheduling tab. If left blank, it will run continuously or when manually processed, depending on the run options configured.

---