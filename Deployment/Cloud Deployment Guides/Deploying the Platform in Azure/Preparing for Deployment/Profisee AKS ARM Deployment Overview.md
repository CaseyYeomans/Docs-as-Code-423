# Profisee AKS ARM Deployment Overview

Deploying the Profisee Platform using Profisee's Azure Kubernetes Services (AKS) ARM template allows an administrator to configure and deploy the Profisee Platform entirely through the Azure web portal. An administrator with valid Profisee and Azure accounts can make use of this quick and easy process for deploying the platform. Assuming you have thoroughly planned your deployment and have completed all of the prerequisite steps, completing the template and deploying the instance can be accomplished in less than two hours.

The Profisee AKS ARM template caters to a variety of the most common deployment scenarios, and we plan to continue to evolve this template as we encounter scenarios that can not be handled. If you encounter a deployment scenario that cannot be supported by this template, please contact [Profisee Support](https://support.profisee.com/aspx/CustomerHome) to capture details of your specific challenges. Alternatively, you can also [Deploy via Powershell Scripts](http:/profiseeplatform/support.profisee.com/wikis/profiseeplatform/aks_deployment), which offers more flexibility/programmability with a tradeoff in complexity.

### How to Plan Your Deployment

The most successful journeys begin with a good plan. The goal of this topic and its related subtopics is to guide you through the various deployment considerations and scenarios and to ensure that you set up all required prerequisites and capture all of the necessary information to complete the ARM template based on your specific deployment scenario and requirements. The figure below illustrates the planning process. Each of the outer planning steps provides the specified information you will need to specify all ARM template properties.
We recommend you maintain a simple text document that captures all the details outlined above, then refer to this document when [Deploying the Platform using the ARM template](https://support.profisee.com/wikis/profiseeplatform/deploying_the_AKS_cluster_with_the_arm_template). ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5b2705b2dbdc2d2c.png)

Before you begin this planning process, you should ensure you and the broader deployment team have all the access rights you need to establish the prerequisites and to run the ARM template. Consult the [Understanding the Required Azure Roles & Permissions](https://support.profisee.com/wikis/profiseeplatform/understanding_the_required_azure_roles_and_permissions) topic to ensure all members of the deployment team have the necessary rights to perform the prerequisite configuration outlined in the planning steps below.

The planning process involves 6 critical planning steps that help identify details of your organization's specific deployment scenario and affect several prerequisite setups that will ensure that your deployment runs successfully. These planning areas are described below:

1. [Planning Your Managed Identity Configuration](https://support.profisee.com/wikis/profiseeplatform/planning_your_managed_identity_configuration) involves making decisions about your Resource Group, DNS, and Azure Active Directory (AAD) that drive roles and permissions that must be configured on the Managed Identity that will be used by the Profisee deployment process.

2. [Planning Your SQL Server Configuration](https://support.profisee.com/wikis/profiseeplatform/planning_your_sql_server_configuration) involves determining if you plan to create a new SQL Server instance related to your cluster or whether you want to use an existing SQL Server instance.

3. [Planning Your File Storage Configuration](https://support.profisee.com/wikis/profiseeplatform/planning_your_file_storage_configuration) involves determining if you plan to create new Azure file storage or whether you want to use existing storage.

4. [Planning Your HTTPS Security](https://support.profisee.com/wikis/profiseeplatform/planning_your_https_security) involves establishing your communication protocol and certificate requirements if needed.

5. [Planning Your Cluster & Network Requirements](https://support.profisee.com/wikis/profiseeplatform/planning_your_cluster_and_network_requirements) involves identifying your cluster name and its network resources and requirements.

6. [Obtaining Your Profisee License & Azure Container Registry (ACR) Credentials](https://support.profisee.com/wikis/profiseeplatform/obtaining_your_profisee_license_and_container_registry_credentials) establishes the information you need to supply to Profisee Support to obtain the licenses necessary for this cluster.

Once you are ready to deploy, you can complete the [Profisee AKS ARM Template](http:/profiseeplatform/github.com/Profisee/kubernetes/tree/master/Azure-ARM) to deploy the Profisee Platform. The topic [Deploying the AKS Cluster with the ARM Template](http:/profiseeplatform/support.profisee.com/wikis/profiseeplatform/deploying_the_AKS_cluster_with_the_arm_template) guides you through the process and gives descriptions and rules for each field within the Custom Deployment template. Once deployment is complete, you can learn how to access your instance of the Profisee Platform with the topic [Logging on to the Profisee Instance](http:/profiseeplatform/support.profisee.com/wikis/profiseeplatform/logging_on_to_the_profisee_instance).

If you encounter errors during the deployment process, refer to [Troubleshooting ARM Deployment Errors and Failures](http:/profiseeplatform/support.profisee.com/wikis/profiseeplatform/troubleshooting_errors_and_failures) for information on resolving them.

### See more

- [Understanding the Required Azure Roles and Permissions](https://support.profisee.com/wikis/profiseeplatform/understanding_the_required_azure_roles_and_permissions)
- [Planning Your Managed Identity Configuration](https://support.profisee.com/wikis/profiseeplatform/planning_your_managed_identity_configuration)
- [Planning Your SQL Server Configuration](https://support.profisee.com/wikis/profiseeplatform/planning_your_sql_server_configuration)
- [Planning Your File Storage Configuration](https://support.profisee.com/wikis/profiseeplatform/planning_your_file_storage_configuration)
- [Planning Your HTTPS Security](https://support.profisee.com/wikis/profiseeplatform/planning_your_https_security)
- [Planning Your Cluster & Network Requirements](https://support.profisee.com/wikis/profiseeplatform/planning_your_cluster_and_network_requirements)
- [Obtaining Your Cluster & Azure Container Registry (ACR) Credentials](https://support.profisee.com/wikis/profiseeplatform/obtaining_your_profisee_license_and_container_registry_credentials)
- [Deploying the AKS Cluster using the ARM Template](https://support.profisee.com/wikis/profiseeplatform/deploying_the_AKS_cluster_with_the_arm_template)
- [Deploying via Powershell Scripts](https://support.profisee.com/wikis/profiseeplatform/aks_deployment)