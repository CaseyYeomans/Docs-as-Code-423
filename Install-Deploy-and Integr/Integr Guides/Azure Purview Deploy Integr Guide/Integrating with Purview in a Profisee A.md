# Integrating with Purview in a Profisee Azure PaaS Environment

Profisee's ARM template for Azure deployment has been extended to support deployment of Profisee's Purview integration. This topic covers the differences in the ARM template as they pertain to Purview. For more detailed guidance on deploying Profisee in Azure, you should refer to the [Profisee AKS ARM Deployment Overview](https://profisee.magentrixcloud.com/wikis/2021_r1_support/deploying_profisee_using_the_arm_template).

For multiple environments, such as Development, Test, and Production, it is recommended to only use one Purview account for all environments with separate Collections for each.

### Selecting Profisee Purview as Your Deployment Image

To install Profisee Purview you must perform the following steps:

1. Prepare for your deployment as you would for deploying the Profisee Platform as described in [Profisee AKS ARM Deployment Overview](https://profisee.magentrixcloud.com/wikis/2021_r1_support/deploying_profisee_using_the_arm_template).
2. Ensure the prerequisites have been met as described in [Prerequisites for Integrating with Purview](https://support.profisee.com/wikis/profiseeplatform/prerequisites_for_integrating_with_purview).
3. Navigate to Profisee's [AKS GitHub Site](https://github.com/Profisee/kubernetes/tree/master/Azure-ARM) and click the **Deploy to Azure** button.
4. Select your Azure **Subscription**, **Resource group**, **Region**, and choose the **User assigned managed identity** you have created to execute the deployment from the **Basics** tab of the ARM template wizard. Then click **Next**to proceed to the**Profisee** tab in the wizard.
5. Choose **[Version].Purview** as the Version of the software to deploy. When this is chosen, you must supply 3 additional settings:

1. **Purview API Url**: This is the Purview (Apache) **Atlas endpoint** that appears in the**Properties** blade of your Purview account in the Azure Portal.
2. **Purview Service Principal ID**: This is the Client ID of your App Registration created as part of the prerequisite setup.
3. **Purview Service Principal Secret**: This is the Client Secret you generated and recorded during the prerequisite setup. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iddad8633a5ac677.png)
6. Complete the rest of the ARM template as described in [Profisee AKS ARM Deployment Overview](https://profisee.magentrixcloud.com/wikis/2021_r1_support/deploying_profisee_using_the_arm_template).
7. Execute and allow the deployment process to complete.

You now have deployed the Profisee platform including integration of the Profisee Platform with Purview and are ready to start propagating your model metadata to Purview using Profisee's **Advanced** and **Adaptive Modeling** functionality.