# Logging on to the Profisee Instance

After a successful deployment of the Profisee Platform using the ARM template, you can immediately log into the Profisee FastApp portal and download FastApp Studio from your deployment output. Once you have accessed your portal and downloaded the desktop client, your deployment and installation process is complete.

1. Navigate to your [Azure portal](https://portal.azure.com/#home) and select **Resource Groups** from the **Azure Services** options.
2. Select the resource group used for deployment.
3. ![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic1bee98aaf6a7df8.png)Click **InstallProfiseePlatform**.
4. Select **Outputs** on the left-hand sidebar.
5. Copy the FastApp Portal web URL within the result, which is contained in quotations after **"WEBURL":**.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ib96a3a3017677952.png)
6. Paste this URL into another browser tab to navigate to your instance of Profisee FastApp portal. You will need to log into the platform using your Profisee username and password.
7. Using the same URL as before, add the endpoint **/api/client**and resubmit. From this page, you can download Profisee FastApp Studio and the Profisee Platform command line tools.

You have now successfully deployed and installed the Profisee Platform. If this deployment does not need to be continually active, you can [stop and start your Profisee instance](https://support.profisee.com/wikis/profiseeplatform/stopping_and_starting_the_profisee_instance) to reduce operating costs. For further operating instructions, refer to the [Profisee Platform Help Guide](https://support.profisee.com/wikis/profiseeplatform/before_you_begin).

### See more

[Stopping and Starting the Profisee Instance](https://support.profisee.com/wikis/profiseeplatform/stopping_and_starting_the_profisee_instance)