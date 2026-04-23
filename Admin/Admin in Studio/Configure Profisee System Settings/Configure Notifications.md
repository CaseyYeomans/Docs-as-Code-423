# Configure Notifications

The table below displays options and functions for Notifications in System Settings. Notifications are sent to users that are assigned a workflow task. Notifications can be further configured for each individual task assignment in the [Workflow administration](https://support.profisee.com/wikis/profiseeplatform/configuring_send_notification_activities) tab.

For more information on setting up OAuth for Office365, see the official Microsoft documentation [here](https://learn.microsoft.com/en-us/exchange/client-developer/legacy-protocols/how-to-authenticate-an-imap-pop-smtp-application-by-using-oauth#use-client-credentials-grant-flow-to-authenticate-smtp-imap-and-pop-connections).

| **Option** | **Function** |
| --- | --- |
| Digest Notification | Configure digest notification using the settings below. |
| Notification Interval | The interval, in minutes, between system checks for unsent digest notifications to send to users. |
| Profisee Notification Digest Number | The maximum number of notification details to include in a notification digest. |
| Email From: Account | The name that displays in the email in the From line of notification emails. |
| Email Notification Templates | Configure text and format for notification emaills using the settings below. |
| HTML Digest Notification | The HTML displayed in digest notification emails. |
| HTML Immediate Notification | The HTML displayed in immediate notification emails. |
| Text Digest Notification | The text displayed in digest notification emails. |
| Text Immediate Notification | The text displayed in immediate notification emails. |
| Email Server | Configure the SMTP server used to send notification emails with the settings below. \**Note: Anonymous authorization is not supported.* |
| Email Port Number | The port number assigned to the email server. |
| Email Server Address | The address of the server used to send notification emails. |
| Email Use SSL | Controls whether TLS encryption is used when the notification server establishes a connection to the email server. Many email servers require TLS encryption. There are two settings: - True - use TLS encryption - False - do not use TLS encryption |
| Email User Name | The email account used to send email notifications to workflow participants. Leave blank if using OAuth. |
| Email User Password | The password associated with the notification email account. Leave blank if using OAuth. |
| OAuth Additional Scopes | The OAuth Additional Scopes used to send email notifications to workflow participants. Leave blank if using username and app-specific password authentication. |
| OAuth Authentication URL | The OAuth Authentication URL used to send email notifications to workflow participants. Leave blank if using username and app-specific password authentication. |
| OAuth Client Secret | The OAuth user secret used to send email notifications to workflow participants. Leave blank if using username and app-specific password authentication. |
| OAuth ClientID | The OAuth ClientID used to send email notifications to workflow participants. Leave blank if using username and app-specific password authentication. |
| Notification Email Link URL | Alternate URL used by the system for creating links in notification emails where the address of the target server is different from the physical address of the primary Profisee web server. This is most often used when a load balancer is used in conjunction with multiple Web server nodes in a Profisee cluster. |
| Profisee Notification Subject | The subject line for Profisee notification emails. |

##

##

There are two methods to configure email notifications, one uses a Username and app-specific password combination, the other uses OAuth.

## Specific Settings for Using a Username and App-Specific Password

- **Email From**: **Account:** sender@contoso.com
- **Email port number:** 587
- **Email server address**: smtp.office365.com
- **Email use TLS**: True
- **Email user name**: sender@contoso.com
- **Email user password**: app-specific password
- **OAuth Additional Scopes**: leave blank
- **OAuth Authentication URL**: leave blank
- **OAuth Client Secret**: leave blank
- **OAuth Client ID**: leave blank

## Specific Settings for Using OAuth with an App Registration and Secret

- **Email From**: **Account:** sender@contoso.com
- **Email port number:** 587
- **Email server address**: smtp.office365.com
- **Email use TLS**: True
- **Email user name**: Leave blank
- **Email user password**: Leave blank
- **OAuth Additional Scopes**: https://outlook.office365.com/.default
- **OAuth Authentication URL**: https://login.microsoftonline.com/<tenant ID>/oauth2/v2.0/token
- **OAuth Client Secret**: the Entra application registration's client secret.
- **OAuth Client ID**: The Entra application registration's client ID.

To complete the OAuth configuration please follow these directions.

1. Create an application registration and name it appropriately. ex. "Profisee Dev SMTP Notifications"
2. Add a new API **Application** type permission for **Office 365 Exchange Online** - **SMTP.SendAsApp**.
3. Have your Entra Global Admin approve the application.
4. Add the account that will be used to send notifications to the **Users and groups** section of the Enterprise Application with the identical name of the application above.
5. Change the **Assignment required** to **Yes** in the Enterprise Application.
6. Have either the Global Admin or Exchange Admin add the following permission to the sending user's mailbox in Powershell:
1. Install-Module -Name ExchangeOnlineManagement #only if missing
2. Import-Module ExchangeOnlineManagement
3. Connect-ExchangeOnline
4. New-ServicePrincipal -AppId <the "Profisee Dev SMTP Notifications" Application Registration Client ID> -ObjectId <the "Profisee Dev SMTP Notifications" Enterprise Application Object ID> -DisplayName "Profisee Dev SMTP Notifications SP"
- example: New-ServicePrincipal -AppId "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" -ObjectId "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" DisplayName "Profisee Dev SMTP Notifications SP"
5. Add-MailboxPermission -Identity <the account from step 4> -User <the "Profisee Dev SMTP Notifications" Enterprise Application Object ID> -AccessRights FullAccess (no lesser permissions exist)
- example: Add-MailboxPermission -Identity "sender@contoso.com" -User "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" -AccessRights FullAccess

You can further lock down the application registration via Conditional Access. Please contact Profisee Support to request our egress IPs.

Note: Profisee is not the sender. We connect to whichever server we are provided, and the actual email originates from that system. Following the above setup; SPF, DKIM, DMARC do not need to be amended. So long as the system we connect to is listed in your SPF record and DKIM has been configured for it, DMARC should validate and emails should be sent and received successfully.