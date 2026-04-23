# Use CLU Options to Stop, Start, and Pause Event Processing

## Switches

The following switches are available to use to start, stop, and pause event processing with :

| Option | Description |
| --- | --- |
| /URL:https://serverName/virtualDirectory | Specifies the connection string to use. |
| /CLIENTID:<Client ID value> | This value can be copied from the account enabled for unattended authentication. |
| /EVENTPROCESSING | Indicates an event processing action will occur. /ACTION is required. |
| /ACTION | Specifies the event processing action to perform. Options include: - **START** Starts the event processing engine when it is in a stopped or paused state. /STARTOPTION is required - **STOP** Halts the processing of events when the engine is in a running or paused state. Events occurring while event processing is stopped are discarded. - **PAUSE** Temporarily halts the processing of events from a running state. Events occurring while event processing is paused continue to be added to the queue of events. Processing will begin with these events when event processing is started again. |
| /STARTOPTION | Specifies how to start processing events. Required with /ACTION:START. Options include: - **LASTPROCESSED** Processing begins with the first transaction added after event processing is was paused. - **FIRST** Processing begins with the first transaction found in the queue. This option is only valid the first time event processing starts. - **DISCARDPRIOR** Processing begins with the first transaction added after event processing is started from a stopped state. |

## Examples

Use the following examples to build your own commands. Change the italicized text to match the corresponding information on your system.

| Task | CLU Command |
| --- | --- |
| Start event processing for the first time | /URL:https://serverName/virtualDirectory /EVENTPROCESSING /ACTION:START /STARTOPTION:FIRST /CLIENTID:<Client ID value> |
| Pause event processing from a running state | /URL:https://serverName/virtualDirectory /EVENTPROCESSING /ACTION:PAUSE /CLIENTID:<Client ID value> |
| Stop event processing from a running state | /URL:https://serverName/virtualDirectory /EVENTPROCESSING /ACTION:STOP /CLIENTID:<Client ID value> |
| Start event processing from a stopped state | /URL:https://serverName/virtualDirectory /EVENTPROCESSING /ACTION:START /STARTOPTION:DISCARDPRIOR /CLIENTID:<Client ID value> |
| Start event processing from a paused state | /URL:https://serverName/virtualDirectory /EVENTPROCESSING /ACTION:START /STARTOPTION:LASTPROCESSED /CLIENTID:<Client ID value> |