# Schedule Housekeeping Using Windows Task Scheduler

Create a task to run housekeeping by running command line options using the Task Scheduler application in Windows.

These are general steps for using Windows Task Scheduler. The specific steps may vary, depending on the version of your operating system.

1. Launch the Windows Task Scheduler.
2. Begin creating a Basic Task.
3. Enter a name and a description of the task, and then click **Next**.
4. Under **When do you want the task to start?**, select how often to run the task, and then click **Next**.
5. Configure the settings for your selection.

Options for this section will vary, depending on the frequency you selected in the previous step.
6. Select **Start a Program** from the option list, and then click **Next**.
7. Click **Browse** to the right of the Program/script field.
8. Do one of the following, depending on how you want to run the command:

- From a batch file

1. Navigate to the batch file where you have saved your command line statement and select it.
2. Click **Next**.
- As a single command

1. Paste the full command line statement into the field.

For example, to purge all expired event messages for all subscriber configurations and scenarios:

Profisee.MasterDataMaestro.Utilities.exe /URL:net.tcp://serverName/maestro/service.svc/tcp /PURGE /TYPE:EVENTS /CLIENTID:<Client ID value>
2. Click **Next**.
- As a command with arguments

1. Navigate to the installation folder for Profisee Utilities, and then select Profisee.MasterDataMaestro.Utilities.exe.

Note: You must install Profisee Utilities to use the CLU options. For more information, see [Install the Command Line Utility](https://support.profisee.com/wikis/profiseeplatform/install_the_command_line_utility).
2. In the Add arguments field, include the parameters you want to include.

For example, to purge all expired event messages for all subscriber configurations and scenarios:

/URL:net.tcp://serverName/maestro/service.svc/tcp /PURGE /TYPE:EVENTS /CLIENTID:<Client ID value>
3. Click **Next**.- Click **Next**.
- Review the settings for the task, and then click **Finish**.