# Profisee SDK Installation

The following instructions apply to new SDK installations only. If you are upgrading from an earlier version of the SDK, it is very important that you refer to the release notes for the specific version you plan to install for migration instructions. The steps can vary depending on the release number.

1. Run ProfiseeSDK.msi.
2. Click **Next** on the setup wizard.
3. On the Destination folder page, choose an install location and then click **Next**.
4. On the Ready to Install Profisee SDK page, click **Install**.
5. If you are using an edition of Visual Studio 2017, and you plan to develop workflows on this computer, select **Run Profisee SDK Workflow Tools Installer** to install the workflow templates in Visual Studio.

If you have an earlier supported version of Visual Studio, the template installation occurs automatically.

**Note**: If you skip this step, you can run the Tools installer manually later on.

1. Click **Finish**.

# Manual SDK Toolbox and Template Installation and Configuration

The necessary tools and templates required for developing workflows are included in the SDK installation setup.

If Visual Studio was not initially installed on the computer where you installed the SDK, or if you have Visual Studio 2017 and you opted to skip installing the Workflow Tools, you can install the toolbox package and workflow templates manually without reinstalling the SDK.

Note that the environments require .NET Framework 4.7.2 or later to use the components.

## Installing the Profisee SDK Visual Studio Toolbox

1. Open the Profisee SDK installation location.
2. Run **Profisee.Services.Sdk.Workflow.PackageInstaller.visx**.
3. Confirm that the correct version of Visual Studio is selected.
4. Click **Install**.
5. Click **Close** to finish the installation.
6. To view the Activities, open a Workflow (\*.xamlx) file in Visual Studio and click in the design area.

## Upgrading Profisee SDK Visual Studio Toolbox

Upgrading the SDK Toolbox requires you to first uninstall the Profisee SDK Toolbox Package from Visual Studio. Note that Visual Studio must be restarted after you have uninstalled the toolbox package.

1. Open Visual Studio.
2. Select **Tools** > **Extensions and Updates**.
3. Select **ToolboxPackage**.
4. Click **Uninstall**.
5. You are prompted to restart Visual Studio.
6. Click **Restart** (you **must** click Restart).
7. Close Visual Studio.
8. Run **Profisee.Services.Sdk.Workflow.PackageInstaller.vsix**.