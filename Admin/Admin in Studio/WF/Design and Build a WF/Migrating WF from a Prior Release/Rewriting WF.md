# Rewriting Workflows

Due to changes to the Profisee Workflow Toolbox, workflows created in Profisee releases prior to 2022.R1 must be rewritten. If the workflows do not contain custom activities, the process is relatively simple and straightforward. If the workflows do contain custom activities, refer to the section at the bottom of this page.

### Rewriting Workflows with No Custom Activities

To rewrite workflows that do not contain custom activities:

1. Create a new environment separate from your existing environment.
2. Uninstall the old Workflow Toolbox for your previous Profisee version. Do **not** uninstall the SDK.
3. Download the SDK for Profisee 2022.R1 and install the 2022.R1 Workflow Toolbox and Workflow Template contained in the SDK in the new environment.
4. Open the existing workflow to be rewritten in Visual Studio.
5. Open the 2022.R1 Workflow Toolbox and create a new workflow template in a separate Visual Studio instance.
6. Recreate the old workflow in the new environment using the updated 2022.R1 activities.

Tips for recognizing updated activities:

Updated activities are labeled "Profisee Platform," where old activities are labeled "Profisee SDK." Additionally, new activities reference "Record Data Context" rather than "Member Data Context."

The previous **CreateBrowseEntityContext** activity has been replaced with **CreateRecordBrowserContext**, and the **NewMemberDataContext** activity has been deprecated.

After you have re-written all workflows, it is recommended to uninstall the old version of the Profisee SDK and retain only the 2022.R1 SDK.

### Replacing Custom Activities with Webhook Activities

If a prior workflow contains a custom activity, it must be replaced with the new Webhook activity introduced in Profisee 2022.R1.

The Webhook activity directs the workflow to an existing web service with an endpoint the workflow can access. Within the logic for this endpoint, you can [create a Webhook](https://docs.github.com/en/developers/webhooks-and-events/webhooks/creating-webhooks) that utilizes the logic used for your previous custom activities to replicate the effect of that custom activity. Note that the web service must be set to authorize a run-as user for the Webhook activity to access the Webhook.

For more information on creating a custom workflow webhook, including a template webhook to use as a basis, please refer to the [Profisee Github page](https://github.com/Profisee/WebhookTemplate) on Webhook Template.