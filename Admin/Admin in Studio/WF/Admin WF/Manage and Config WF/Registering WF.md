# Registering Workflows

After you develop a workflow with Visual Studio, you must register that workflow with the Profisee Platform using workflow administration in Profisee FastApp Studio.

The registration process transfers the runtime components from your development environment to the workflow file repository configured for the target platform environment. During registration, the workflow .XAML file is parsed, and the configurable activities included in the workflow are saved to the database so they can be configured for the target test environment.

To register a workflow

1. Click **Workflow** under the Administration tab.
2. Click **Register**in the Workflow toolbar beneath the Workflow system tab.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i761a0b1b8d1c068.png)

The Register Workflow dialog appears.![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i3540895fb41f405f.png)
3. Click the **Open** icon to the right of the Workflow Project File field.
4. Select the workflow project file (.csproj extension) that contains the workflow you wish to register, then click **Open**.
5. Click the **Configuration** dropdown and select a configuration.

This will typically have **Debug** and **Release** options, but there could be other options depending on your specific development configuration setup. When registering for a production environment, Profisee recommends deploying the **Release** configuration because build optimizations in release will yield better performance.

6. Click the Workflow File dropdown and select a .XAML file from the list that contains the workflow definition you want to register.
7. Click **Register**.

When a new version of an existing workflow is registered, the configuration from the prior version is used for the version and each of the version's configurable activities where the activities match exactly by name. If new configurable activities are added, you must explicitly configure these after the registration is complete.

The **Workflow summary information** panel displays the following information about the registered workflow.

- **Workflow Name**:Displays the name of the .XAML file from which the workflow originated.
- **Activity grid**: Displays the name and activity type for each of the workflow's configurable activities.

- A green check mark indicates an identical activity
- A red X indicates a deleted activity
- A blue plus indicates a net new activity![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-ia39459bfc9348fd2.png)

8. Click **Close** to return to the **Workflow** tab. The new workflow version is added to the workflows and versions grid.

You can now continue to the next step and [configure](https://support.profisee.com/wikis/profiseeplatform/configure_a_workflow) your workflow and activities.