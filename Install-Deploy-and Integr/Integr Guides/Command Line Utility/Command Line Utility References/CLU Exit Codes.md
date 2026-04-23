# CLU Exit Codes

Identify and resolve unexpected errors in your overall batch process using exit codes.

| Exit Code | Meaning |
| --- | --- |
| 0 | There was an error running the command. |
| 1 | The command completed with no errors. |

Example using exit codes in a command running a strategy:

SET Utilities="C:\Program Files\Profisee\Master Data Maestro Utilities\7.0\"

%Utilities% /URL:https://myServer/myPath /PROCESSMATCHING /<Strategy Name> /CLEARALLPRIORRESULTS /*CLIENTID:<Client ID value>*

if "%errorlevel%"=="1" Echo Success

if "%errorlevel%"=="0" Echo Fail