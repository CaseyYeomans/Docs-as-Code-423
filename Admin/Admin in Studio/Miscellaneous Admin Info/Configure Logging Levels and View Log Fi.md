# Configure Logging Levels and View Log Files

When a message is logged to an application or service's log file, that message is tagged with a logging level that indicates the severity of the message. You can individually configure each application or service to only catch messages of a certain severity or higher. The logging levels from least to most severe are:

1. **Verbose**:Verbose is the noisiest level, rarely (if ever) enabled in a production environment.
2. **Debug**: Debug is used for internal system events that are not necessarily observable from the outside, but useful when determining how something happened.
3. **Information**: Information events describe things happening in the system that correspond to its responsibilities and functions. Generally these are the observable actions the system can perform.
4. **Warning**: When service is degraded, endangered, or may be behaving outside of its expected parameters, Warning level events are used.
5. **Error**: When functionality is unavailable or expectations broken, an Error event is used.
6. **Fatal**: The most critical level, Fatal events demand immediate attention.

If an application or service's logging level is set to Verbose, it will log messages of all severity. If its logging level is set to Fatal, it will only log critical errors. If it is set to Warning, it will log warnings, errors, and fatal error messages.

To configure the logging level for an application or service, you must change the minimum log level line within its configuration file.

1. Navigate to the folder containing the application or service whose logging level you want to configure.
2. Open the configuration file for that program.\*
3. Locate the Minimum Log Level line. This line is set to **Warning** by default.
4. Replace **Warning** with your desired logging level.
5. Save changes and close the configuration file.
6. Restart the service.
- Restart Windows service for Service Host.
- Restart IIS Application Pool for all other services, API gateway, and web portal.

*\*Host and Configuration Manager log to the same LogFiles folder.*

### Configuration File Locations

| | | | | |
| --- | --- | --- | --- | --- |
| **Application Name** | **Default Configuration File Location** | **Default Log File location** | **Default Log Level Line** | |
| **Service Host** | C:\Program Files\Profisee\Master Data Maestro Server\21.3.0\Services\Monolith\Profisee.MasterDataMaestro.Host.dll.Config | C:\Program Files\Profisee\Master Data Maestro Server\8.1.0\LogFiles **Or** C:\Users\<Service User>\AppData\Roaming\Profisee\LogFiles **Depending on user permissions** | <add key="ProfiseeAppSettings:MinimumLogLevel" value="Warning" /> | |
| **Workflow Service** | C:\Program Files\Profisee\Master Data Maestro Server\8.1.0\Services\Workflows\appsettings.json | C:\Program Files\Profisee\Master Data Maestro Server\8.1.0\Services\Workflows\LogFiles | "MinimumLogLevel": "Warning" | |
| **File Attachment Service** | C:\Program Files\Profisee\Master Data Maestro Server\8.1.0\Services\Attachments\appsettings.json | C:\Program Files\Profisee\Master Data Maestro Server\8.1.0\Services\Attachments\LogFiles | "MinimumLogLevel": "Warning" | |
| **FastApp Studio Client** | C:\Program Files\Profisee\Master Data Maestro Desktop\8.1.0\Profisee.MasterDataMaestro.UI.exe.config | C:\Users\<user>\AppData\Roaming\Profisee\<assembly version>\<assembly name>\LogFiles | <add key="ProfiseeAppSettings:MinimumLogLevel" value="Warning" /> | |
| **API Gateway** | C:\Program Files\Profisee\Master Data Maestro Server\{version}\Gateway\Web.Config | C:\Program Files\Profisee\Master Data Maestro Server\8.1.0\Web\LogFiles | <add key="ProfiseeAppSettings:MinimumLogLevel" value="Warning" /> | |
| **Web Portal** | C:\Program Files\Profisee\Master Data Maestro Server\8.1.0\WebPortal\Web.Config | C:\Program Files\Profisee\Master Data Maestro Server\8.1.0\WebPortal\LogFiles | <add key="ProfiseeAppSettings:MinimumLogLevel" value="Warning" /> | |
| **Utilities - CLU** | C:\Program Files\Profisee\Master Data Maestro Utilities\8.1.0\Profisee.MasterDataMaestro.Utilities.exe.Config | C:\Program Files\Profisee\Master Data Maestro Utilities\8.1.0\LogFiles **Or** C:\Users\<Service User>\AppData\Roaming\Profisee\LogFiles **Depending on user permissions** | <add key="ProfiseeAppSettings:MinimumLogLevel" value="Warning" /> | |
| **Configuration Manager** | C:\Program Files\Profisee\Master Data Maestro Server\8.1.0\Profisee.MasterDataMaestro.Host.dll.Config | C:\Program Files\Profisee\Master Data Maestro Server\8.1.0\LogFiles | <add key="ProfiseeAppSettings:MinimumLogLevel" value="Warning" /> | |
| **Authentication Service** | C:\Program Files\Profisee\Master Data Maestro Server\8.1.0\Services\Auth\appsettings.json | C:\Program Files\Profisee\Master Data Maestro Server\8.1.0\Services\Auth\LogFiles | "MinimumLogLevel": "Warning" | |

Configuration files are read-only and require administrator privileges to edit.