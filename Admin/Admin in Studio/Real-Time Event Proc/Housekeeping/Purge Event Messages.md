# Purge Event Messages

To add a purge task to Housekeeping, you must run a purge request from the command line using the Profisee CLU. Event messages exceeding the Event message retention days value are affected by purge requests.

To purge all qualifying event messages:

Profisee.MasterDataMaestro.Utilities.exe /URL:net.tcp://serverName/maestroWebApplication:portNumber /PURGE /TYPE:EVENTS

To purge all qualifying event messages for a specific external subscription:

Profisee.MasterDataMaestro.Utilities.exe /URL:net.tcp://serverName/maestroWebApplication:portNumber /PURGE /TYPE:EVENTS /EXTERNALSCENARIO:"scenarioName"

Use your Profisee server connection string as the argument for the /URL switch. The syntax for this string will vary, depending on your server setup.

The /PURGE switch option sends a purge request to the server. A purge is requested for all subscriptions according to the system-defined retention period configured in the Profisee server when no subscription is specified.

Event purging does not occur periodically unless a purge request is scheduled in addition to the housekeeping request. Event purging can be scheduled to run on a periodic basis by:

- Creating a scheduled event using the Windows Task Scheduler (or another scheduler)
- Using the CLU to execute the command line above

For more information on using the Command Line Utility, see [Use the Command Line Utility](https://support.profisee.com/wikis/profiseeplatform/use_the_command_line_utility).

For more information on using the CLU to purge event messages, see [Housekeeping CLU reference](https://support.profisee.com/wikis/profiseeplatform/housekeeping_clu_reference).