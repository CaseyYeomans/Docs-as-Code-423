# Integrating Fabric with Profisee

Welcome to introduce Profisee Master Data Management (MDM) for Microsoft Fabric! This new integration allows users to leverage native MDM capabilities within Fabric, powered by Profisee.

With this update, Profisee users can seamlessly access core MDM functions directly within Microsoft Fabric, making it easier than ever to model and manage master data. While initial capabilities focus on data modeling and stewardship, future updates will continue to expand Profisee's functionality within Fabric. Changes made in Fabric persist into Profisee.

If you don't have an existing Profisee instance, Microsoft Fabric users can access a free trial version. This trial provides a pre-configured environment where you can explore basic Data Stewardship and Data Modeling capabilities--a low-friction way to experience Profisee's MDM features firsthand.

### Getting Started

- **Admins**: Before enabling Profisee MDM for your organization, please review the **Profisee and Fabric Workload Deployment** steps below.
- **Users**: If your organization has already set up Profisee in Fabric, skip ahead to **Creating a Profisee Data Product** to get started.

If you are using a non-SaaS deployment of Profisee, administrators must take the [additional steps outlined here](https://support.profisee.com/wikis/profiseeplatform/integrating_a_non-saas_instance_with_fabric) before Fabric integration can begin.

## Profisee and Fabric Workload Deployment (Administrators)

Before your organization can access Profisee MDM, an administrator must configure the Fabric workload for use with Profisee. To successfully use Profisee's Fabric workload, please follow the steps below and make the necessary changes in Fabric to approve the workload there.

1. Ensure that your fabric account has **Global Admin** permissions. A Fabric-only Admin cannot approve the Profisee Fabric App registration permissions.
2. Go to the [**Fabric Homepage**](https://app.fabric.microsoft.com) > **Workloads** (left) > **More workloads** > **Profisee MDM (preview)** > **Add Workload**.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i74017fdcbd7a5b29.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-icd60cdcbc7c1405b.png)
3. Add the workload to a premium capacity when prompted.

If you do not have an existing capacity, you will need to create one.

Check which region is your Fabric home region by going to the [Fabric Homepage](https://app.fabric.microsoft.com), then clicking top right on the question mark, then **About Fabric**. Your region is listed at the bottom of the popup.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i48d79de9f3d911bf.png)
Create a Fabric Premium capacity in the same region. There may be some delay between capacity creation and the ability to select it. Refresh the page after a few minutes if it does not appear immediately.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i536bebb74e56e1a3.png)
Once the capacity is available, select it and continue to the next step.

4. Click **Add Workload**, then click **Continue**when prompted by the **Additional authentication...** popup.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id17968bf5d8c95e9.png)
5. Approve the permissions needed by the Fabric workload in your tenant when prompted. Once approval has been granted, the **Add Workload** button changes to **Manage Capacities**.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i523df416a2889524.png)

You may decide whether or not to select the **Consent on behalf of your organization** option when prompted. If the Global Admin does not consent to the required permissions, individual users will be prompted to instead. Depending on your organization's security posture and internal requirements, you may or may not be permitted to grant GA consent. Please consult internally which approach best fits your organization.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic078965ca1a70952.png)
If this option is not selected, see **Permissions** below.

### Permissions

If Global Admin Consent is not granted across the organization, each individual user must accept the following permissions before using Fabric:

- **Azure Storage, user\_impersonation** - Access Azure storage on behalf of the signed-in user.
- **Microsoft Graph, User.Read** - Standard permission that grants access to the user's information.
- **Power Bi Service, Fabric.Extend** - Extends Fabric with new item types. This is required for the workload as it creates a new item type (the Profisee Data Product, accessible through the Fabric UI).
- **Power Bi Service, Workspace.Read.All** - View all workspaces, required to view workspaces in Fabric.

### Adding Additional Workspaces

If needed, a Fabric Admin can add additional Workspaces to the Premium capacity by navigating to **Settings** >**Admin Portal** > **Workspaces** > **Workspace settings** > **Reassign workspace**. From here, select the Capacity that the Workload is deployed to.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i1e2e38662237b069.png)

## Creating a Profisee Data Product (Users)

After the Fabric workspace has been configured, users must select the correct workspace to create a Profisee MDM item within, then create a Data Product to begin their Profisee integration.

1. Navigate to the [Microsoft Fabric homepage](https://app.fabric.microsoft.com/home).
2. Go to **Workspaces**, then select the workspace that has been configured for a Profisee MDM workload.
This workspace must show the diamond icon next to it, signifying that it is backed by Premium Capacity. Contact your organization's Fabric Administrator if you do not know which workspace to select.
3. Click **New item**, then click the filter in the top right and type **Profisee**. Optionally, click the star to mark it as Favorite for future use.
4. Select the Profisee item.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i65d87e1258844d93.png)
5. Create a new Profisee Data Product by inputting a name for the Data Product, and clicking the **Create** button. The Data Product opens and prompts you to connect to a Profisee instance.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i4576314e0c7eb18d.png)
6. Click the **Connect** button.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i6d5370d6d91b66a7.png)
7. Open the Profisee Instance dropdown and select **Paste URL...** to add the address of your Profisee instance OR select an existing instance OR select the **Proceed with a Free Trial Version** option to gain access to a limited trial version of Profisee.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i552d3bdf4f5679a1.png)
8. Click **Connect**.

Now that your Profisee and Fabric environments are connected, you can create new entities under your Data Product, or connect the Data Product to existing entities.