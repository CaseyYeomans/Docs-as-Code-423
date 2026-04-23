# Additional Monitoring using Hangfire

While using Monitor, you may note certain properties allow you to navigate out of Profisee Portal and onto Hangfire. Hangfire is an external platform that allows you additional insight into the monitoring process by displaying detailed information on running processes.

Each activity has a link under the **Details** heading which will redirect you to Hangfire for additional monitoring information. Clicking any external links to Hangfire will bring you to the Hangfire batch landing page in a new window, where you can view information on processes running in your Profisee instance. You must have Super Administrator privileges to access this page.

This landing page displays detailed status information related to the monitored activity. You also have the ability to navigate to other running activities connected to Hangfire from your Monitor instance. This information can be useful for resolving support cases or engaging in specific troubleshooting scenarios, and will likely not be necessary for standard monitoring procedures.

For more information, refer to the [Hangfire online documentation](https://docs.hangfire.io/en/latest/).

When restarting any service during maintenance or configuration, all web browsers with Hangfire windows open must be closed to allow for the service to start in a healthy state.

Note that a hangfire detail may display the message <VALUE IS TOO BIG>. This does not indicate an error and can be ignored.