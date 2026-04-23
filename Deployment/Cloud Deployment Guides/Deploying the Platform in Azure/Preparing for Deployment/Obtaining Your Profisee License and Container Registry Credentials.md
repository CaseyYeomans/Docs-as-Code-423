# Obtaining Your Profisee License and Container Registry Credentials

When completing the Profisee ARM template, you will need to supply a Profisee License, Profisee ACR User Name, and Profisee ACR Password. The Profisee ACR User Name, and Profisee ACR Password are required to access Profisee's Azure Container Registry (ACR) and the Profisee License is required to license the Profisee Platform. These credentials can be obtained by contacting Profisee support at [support.profisee.com](https://support.profisee.com/aspx/CustomerHome).

You must do the following to create and use your Profisee credentials:

1. Navigate to the [Profisee Support](https://support.profisee.com/aspx/ProfiseeCustomerHome) portal and click [Support](https://support.profisee.com/Force/force__case/index) on the header toolbar.
2. Open a new ticket and select "I have a license question" as the Case Reason.
3. Provide Profisee support with the DNS URL for the environment you are creating.
This URL must match the one that you will use for the ARM template, and should be given in the format: *https://server.domain.com*.
4. Save the credentials received from customer support.
These credentials will be required to complete the **Profisee License**, **Profisee ACR User Name**, and **Profisee ACR Password** properties of the ARM template.

You are now ready to complete the ARM template and [deploy the Profisee Platform with Azure Kubernetes Services](https://support.profisee.com/wikis/profiseeplatform/deploying_the_AKS_cluster_with_the_arm_template). Ensure all required information from the prior planning topics has been recorded and is easily accessible, then navigate to the [Kubernetes section of the Profisee GitHub](https://github.com/Profisee/kubernetes/tree/master/Azure-ARM) and click **Deploy to Azure** to begin the deployment process.

### See more

- [Profisee AKS ARM Deployment Overview](https://support.profisee.com/wikis/profiseeplatform/deploying_profisee_using_the_arm_template)
- [Deploying the AKS Cluster using the ARM Template](https://support.profisee.com/wikis/profiseeplatform/deploying_the_AKS_cluster_with_the_arm_template)