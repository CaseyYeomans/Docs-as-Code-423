# Migrating an On-Premise Database to PaaS

If you have an existing on-premise installation of the Profisee platform, you can migrate your installation to a PaaS deployment. Doing so retains all record data, system configurations, and other specifications from your existing installation. If you want to move from an on-premise installation to a PaaS solution:

1. Delete any service accounts from your Profisee installation.
2. Remove any staging tables from your current Profisee installation. *If you are using Profisee Platform version 2021.R3 or higher, you may skip this step*

If you would like to retain your current staging tables to use in your PaaS deployment, you can export your staging tables in Profisee FastApp Studio, then import them into your new installation after deployment.

3. Locate your Profisee database in your database management software (SQL, AWS, Azure, etc) and deploy it to Azure SQL.

For most database management software, this can be done by right-clicking your database and selecting an option labeled "Deploy database to Azure SQL" or something similar. Refer to your database management software documentation for detailed instructions.

4. Delete any "phantom databases" that are left behind after migration. These "phantom databases" will not impact deployment, but they may appear in menus after deployment, causing confusion to users down the line.

After these prerequisite steps have been observed, you may begin your [AKS deployment](https://support.profisee.com/wikis/profiseeplatform/deploying_the_AKS_cluster_with_the_arm_template) as usual, selecting the above database as the database to deploy. After deployment, you may safely re-add any removed service accounts and import any staging tables that were removed for migration.