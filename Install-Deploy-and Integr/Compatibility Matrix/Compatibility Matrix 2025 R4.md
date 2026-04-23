# Compatibility Matrix 2025 R4

##

# Profisee Compatibility

Use the following table to determine the versions of the SDK, Integrator, and Microsoft SQL RDBMS to use with a specific version of the Profisee Platform.

| | | | | | | |
| --- | --- | --- | --- | --- | --- | --- |
| For this Profisee version: | Use these software versions: | | | | | |
| **Profisee SDK** | **Integrator** | **SQL Server Master Data Services** | **SQL Server RDBMS** | **Text Writer Event Subscriber** | **MMU** |
| **2024 R1** | 2024 R1 | 4.2.1 | n/a | 2017 2019 2022 Azure SQL DB (140, 150, 160) | 1.1.1 | MMU 1.3.0 |
| **2024 R2** | 2024 R2 | 4.2.1 | n/a | 2017 2019 2022 Azure SQL DB (140, 150, 160) | 1.1.1 | MMU 1.3.0 |
| **2025 R0** | 2025 R0 | 4.2.1 | n/a | 2017 2019 2022 Azure SQL DB (140, 150, 160) | 1.1.1 | MMU 1.3.0 |
| **2025 R1** | 2025 R1 | 4.2.1 | n/a | 2017 2019 2022 Azure SQL DB (140, 150, 160) | 1.1.1 | MMU 1.3.0 |
| **2025 R2** | 2025 R2 | 4.2.1 | n/a | 2017 2019 2022 Azure SQL DB (140, 150, 160) | 1.1.1 | MMU 1.3.0 |
| **2025 R3** | 2025 R3 | 4.2.1 | n/a | 2017 2019 2022 Azure SQL DB (140, 150, 160) | 1.1.1 | MMU 1.3.0 |
| **2025 R4** | 2025 R4 | 4.2.1 | n/a | 2017 2019 2022 Azure SQL DB (140, 150, 160) | 1.1.1 | MMU 1.3.0 |

# Integrator/Federation Manager Compatibility

Use the following table to determine the connector versions to use with a specific version of Integrator.

| | | | | | | | | | |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **For this connector:** | **Use this combination of connector version and Integrator version:** | | | | | | | | |
| **4.2.1** |
| **SQL Server** | 4.2.1 |
| **Azure SQL Server DW** | N/A |
| **File** | N/A |
| **Dynamics CRM** | 4.2.1 |
| **Dynamics AX** | N/A |
| **Salesforce** | 4.3.1 |
| **Maestro** **Server** | N/A |
| **Dun &** **Bradstreet** | N/A |
| **MelissaData Personator** | N/A |
| **Active** **Directory** | N/A |
| **SAP** | N/A |
| **Excel** | 4.1.1\* |
| **Oracle** **Database** | N/A |
| **D365FO** | 1.4.1 |
| **Profisee** | 4.5.0\*\* |
| **Dun & Bradstreet Direct+** | 1.1.1 |
| **CRM IFD** | N/A |

*\*Excel Connector 4.1.1 cannot be triggered via Eventing*
*\***\*This connector is not available with Integrator 4.2.1, and must be installed via an available patch*
*Connectors marked 'N/A' are not included in installation and are not compatible with Eventing.*

# Use the following table to determine the correct connector to use with a specific application server version. This is based on the latest available version of integrator.

# Connector Compatibility

| | |
| --- | --- |
| **This connector:** | **Is compatible with these application versions:** |
| **SQL Server\*** | SQL Server 2012-2017 Azure SQL DB (Current Release) |
| **Azure SQL Server DW** | Current Release and Sandboxes |
| **File Connector** | N/A |
| **Dynamics CRM** | CRM 2011, 2015, 2016, Online (Current Release) |
| **Dynamics AX** | AX 2012 R3 |
| **Dynamics CRM IFD** | CRM 2011, 2015, 2016, Online (Current Release) |
| **Salesforce** | Current Release and Sandboxes |
| **Dun & Bradstreet** | Direct 2.0 |
| **MelissaData Personator** | Current Release and Sandboxes |
| **Active Directory** | Server 2012 or later |
| **SAP** | SAP ECC 6 |
| **Microsoft Excel** | Excel 7.0 and higher. |
| **Oracle Database** | Any version of Oracle compatible with Oracle Managed Data Access Component version 4.122 |
| **Microsoft MDS** | MDS 2014, 2016, & 2017 |
| **OData** | OData 2.0 |
| **Dynamics 365 FO** | Enterprise Edition |

**\*Composite key support for SQL is added in version 4.1.0**

Profisee SDK Compatibility

A new version of the Profisee(R) SDK is released for each new version of Profisee. Refer to the SDK release notes for specific versions for upgrade details.

| | |
| --- | --- |
| **This version of the Profisee SDK:** | **Is compatible with these versions of Visual Studio:** |
| **6.0.2 R1 and later** | Professional and Enterprise Editions: VS 2017 VS 2019 VS 2022 Community Editions: VS 2017 VS 2019 VS 2022\* |

*\***Visual Studio 2022 for ARM64 is not compatible with the Profisee SDK*

Profisee Connect Compatibility

The following service providers are compatible with the Profisee Portal Connect feature by default.

| | |
| --- | --- |
| **Profisee Version** | **Service Providers** |
| 2024.R1 | **Melissa Data Personater API version 3** |
| 2024.R2 | **Melissa Data Personater API version 3** |
| 2025.R0 | **Melissa Data Personater API version 3** **SQL Server Database** (Requires additional configuration) **OneLake Database** (Requires Additional Configuration) |
| 2025.R1 | **Melissa Data Personater API version 3** **Synapse** **SQL Server Database** (Requires additional configuration) **OneLake Database** (Requires Additional Configuration) **Databricks** (Requires additional configuration) **Snowflake** (Requires Additional Configuration) |
| 2025.R2 | **Melissa Data Personater API version 3** **Synapse** **SQL Server Database** (Requires additional configuration) **OneLake Database** (Requires Additional Configuration) **Databricks** (Requires additional configuration) **Snowflake** (Requires Additional Configuration) |
| 2025.R3 | **Melissa Data Personater API version 3** **Synapse** **SQL Server Database** (Requires additional configuration) **OneLake Database** (Requires Additional Configuration) **Databricks** (Requires additional configuration) **Snowflake** (Requires Additional Configuration) |
| 2025.R4 | **Melissa Data Personater API version 3** **Webhook** **D&B Identity Resolution** **D&B Company Information** **D&B Hierarchies and Connections** **Synapse** **SQL Server Database** (Requires additional configuration) **OneLake Database** (Requires Additional Configuration) **Databricks** (Requires additional configuration) **Snowflake** (Requires Additional Configuration) |

## Deployment-Specific Feature Compatibility

- Adaptive cards for the Share Record to Teams and Outlook feature are only available in SaaS-based deployments.
- Integration with Fabric is available for all deployment styles from any version of Profisee 2025 R0 and onward.