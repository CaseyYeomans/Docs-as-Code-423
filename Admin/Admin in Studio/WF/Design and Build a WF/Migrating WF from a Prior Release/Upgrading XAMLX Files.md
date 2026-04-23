# Upgrading XAMLX Files

NOTE: Unless you are using a Source Code Control System (SCCS), create backups of your .xamlx files; the files will be overwritten during the upgrade process. Profisee strongly recommends using an SCCS for managing source code for all custom development using the SDK.

Previous versions of the MaestroWorkflowService.xamlx files must be upgraded using the utility *Profisee.Services.Sdk.UpgradeUtilities.exe* before being republished and registered. This utility automatically replaces references in the .xamlx files with the appropriate references for the current release.

To upgrade your \*.xamlx files and MaestroWorkflowService project:

1. Open a Command Prompt window.
2. Navigate to the location of the Profisee SDK installation directory. By default, it is located here: *%programFiles%\Profisee\Master Data Maestro SDK\[Version]*
3. Type *Profisee.Services.Sdk.UpgradeUtilities.exe* at the prompt, including the applicable switches and information as follows:

- /XAMLX - Specifies XAMLX as the target type for the command
- /FILE - The path to the directory where the \*.xamlx files are located
- /RECURSIVE - Optional parameter used with a file directory to iterate and upgrade all \*.xamlx files under the specified directory

**Example**: Profisee.Services.Sdk.UpgradeUtilities.exe /XAMLX /FILE:"C:\filePath" /RECURSIVE

Pressing Enter after typing Profisee.Services.Sdk.UpgradeUtilities.exe displays help for the command and all switches.