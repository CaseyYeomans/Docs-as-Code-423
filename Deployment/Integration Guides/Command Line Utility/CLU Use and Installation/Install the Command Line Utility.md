# Install the Command Line Utility

Import and export model metadata, lists, views, strategies and rules from a command prompt or in any ETL tool with the Profisee Command Line Utility (CLU). Install the tool on the server where the Profisee Server application is installed, or on a remote client machine. When installing the CLU remotely, copy the installation files from the server directory to the client and install in the remote location.

Installing the Command Line Utility is a separate step performed after the Profisee Server installation is complete. To install the Command Line Utility:

1. Navigate to the ToolsInstaller.msi file in the Profisee Server installation folder. If Profisee Server was installed using the default path, you can find the file in the following location:

C:\Program Files\Profisee\Master Data Maestro Server\8.1.0\Web
2. Double-click the ToolsInstaller.msi file to open the setup wizard.
3. Click **Next** to start the installation process.
4. Enter a custom installation location for the utility, or use the default path provided in the dialog.
5. Click **Next**.
6. Click **Install**.
7. Click **Finish** when the installation is complete.

When you upgrade your Profisee server, you must uninstall the previous CLU version and run the new ToolsInstaller.msi to install the compatible version of the CLU.