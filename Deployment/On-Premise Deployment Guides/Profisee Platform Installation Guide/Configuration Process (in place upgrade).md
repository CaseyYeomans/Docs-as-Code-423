# Configuration Process (in place upgrade)

Upgrade an existing database and Web application in place if you want users to automatically receive the upgraded FastApp Studio client and use the upgraded Server the next time they connect. Use Configuration Manager to select an existing Profisee database and upgrade it to the new release.

![](https://Profisee.magentrixcloud.com/contents/assets/images/ExclamationMark.png) Before upgrading an existing application, ensure that you have made a full backup of the Profisee database. The database upgrade process is not reversible.

![](https://Profisee.magentrixcloud.com/contents/assets/images/ExclamationMark.png) Before upgrading an existing application, ensure that there are no matching or address verification strategies in an invalid state. Correct or delete invalid strategies prior to the upgrade to avoid errors.

![](https://Profisee.magentrixcloud.com/contents/assets/images/ExclamationMark.png) For multi-node clusters, remove instances on all secondary server nodes before removing the primary server node instance.

1. Using SQL Server Management Studio, create a full backup of the existing database immediately before the upgrade.
2. Remove the existing instance in Configuration Manager (using the prior version):
1. Select **Edit an Existing Instance**
2. Ensure that the correct Profisee instance is selected in the drop-down.
3. Click **Remove this Instance**.
4. Exit when finished.
3. Create a new Instance in Configuration Manager (using the updated version):
1. Create the Profisee Web application and proceed through the Configuration process as described in the [new installation instructions](https://support.profisee.com/wikis/profiseeplatform/configuration_manager_new_installation). Reuse the prior Profisee application name so that users will be able to reconnect to the same URL.
2. On the Select Databases page, select the existing Profisee database to upgrade. The **Upgrade existing database** checkbox should be checked by default, indicating that Profisee has detected the need to upgrade.
3. Click **Next** to continue through the Configuration process to the Progress and Finish page. You will see the Web application created and the Profisee database upgraded.
4. The application is now ready to use.

![](https://Profisee.magentrixcloud.com/contents/assets/images/ExclamationMark.png) If your Profisee Server environment currently supports custom interfaces built with the Profisee SDK (including workflows, custom web applications, and service bus integration facilities), you must consider the upgrade requirements of these customizations as well. Such upgrades are beyond the scope of what can be documented here. Guidelines and considerations for upgrading the Profisee SDK and your related customizations can be found in the release notes associated with the Profisee SDK that matches the release of Profisee Server to which you are upgrading.

![](https://Profisee.magentrixcloud.com/contents/assets/images/ExclamationMark.png)During the upgrade process, ensure you do not re-use an old folder location for your previous instance, as it may contain subscriber DLLs from older versions.

Any time you run through Configuration Manager on the primary server, you must also run through Configuration Manager on all nodes in the cluster. Failure to do so will cause errors to occur on nodes that have not been reconfigured.