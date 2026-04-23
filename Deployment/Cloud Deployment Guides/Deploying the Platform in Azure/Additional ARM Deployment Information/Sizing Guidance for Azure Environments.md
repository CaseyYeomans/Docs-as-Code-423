# Sizing Guidance for Azure Environments

When determining the resources needed to deploy the Profisee Platform, refer to the [System Requirements for Profisee Server](https://support.profisee.com/wikis/profiseeplatform/system_requirements_for_profisee_server_24r2) topic found in the general installation guide. Profisee has not found any material difference in normal web server performance between an Azure environment and an on-premise environment, but we believe there are material differences in performance for SQL Server.

For your processing server, use the general on-premise sizing guide found under **Web Application and Processing Servers** in the topic above.

For SQL Server, ensure that your SQL server size is set to the upper end (or above) of what we would recommend for an on-premises environment under **Database Servers** in the topic above. Note that even with a larger SQL Server size, you may encounter moderately lower SQL Server performance compared to an on-premise environment.