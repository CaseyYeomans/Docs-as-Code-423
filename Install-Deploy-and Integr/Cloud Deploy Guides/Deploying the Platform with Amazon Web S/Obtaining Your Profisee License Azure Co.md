# Obtaining Your Profisee License Azure Container Registry Credentials

When performing a Profisee Platform Platform-as-a-Service (PaaS) deployment, you will need to configure the **Settings.yaml** file with a Profisee License and Azure Container Registry (ACR) username and password. The Profisee ACR username and password are required to access Profisee's ACR to download the container image while the license is required to operate the Profisee Platform. A license and your ACR credentials can be obtained by contacting [Profisee Support](https://support.profisee.com).

You must do the following to create and use your Profisee credentials:

- Navigate to the [Profisee Support](https://support.profisee.com) portal and click **Support** on the header toolbar.
- Open a new ticket and select **I have a license question** as the **Case Reason**.
- Provide Profisee support with the **External DNS URL** for the environment you are creating along with the version of software you are intending to run. Refer to the **External DNS URL** you specified during [Planning Your Cluster & Network Configuration](https://support.profisee.com/wikis/profiseeplatform/planning_your_cluster_and_network_configuration).

If you are a prospect considering Profisee and do not yet have a login to the Profisee Customer Portal, work with your account executive to obtain an evaluation license and ACR credentials.

Save the license and ACR credentials you received from customer support in a safe location you can reference when going through the planning and deployment process. These credentials will be used to update your **Settings.yaml** file you prepare prior to deployment execution. These settings are in two sections in the .yaml file:

1. The **image** section of **Settings.yaml** identifies the location of the Profisee ACR, the container image you want to deploy, and the credentials that you need to use to access the ACR. You need to add your assigned username and password to the .yaml file as shown below:
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ie90cd255d1b50517.png)
2. The **licenseFileData** contains the text associated with the encoded license that you received from Profisee Support. This text must be copied and pasted in the supplied license (.txt) file as shown below:
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i34767c60514a32c6.png)

Your **Settings.yaml** file is now complete and you are now ready to execute the cluster deployment steps outlined in [Deploy Profisee platform on to AWS Elastic Kubernetes services (EKS)](https://github.com/Profisee/kubernetes/tree/master/AWS-EKS-CLI).