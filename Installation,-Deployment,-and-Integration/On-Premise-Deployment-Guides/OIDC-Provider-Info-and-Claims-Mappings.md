# OIDC Provider Info and Claims Mappings

When configuring the Profisee server to use an OpenID Connect (OIDC) provider, you must map certain claims from your OIDC provider to your Profisee account properties. The Profisee account properties that must be mapped include:

* **User Name:**For most OpenID Connect providers, this is the email address the user uses to login.
* **User ID:**This is the unique internal identifier for the users account, and is often in the form of a GUID.
* **First Name:**The first name of the user
* **Last Name:**The last name of the user
* **Email Address:** The email address of the user. This claim is often the same as the User Name claim.

The following list contains the default Claims Mappings and Client IDs for commonly used OIDC providers. Some OIDC providers allow for customization of claim definitions and values, which will require you to work with the administrator of your OIDC provider to get the correct claims values if they’ve been modified from the defaults below.

If your OIDC provider is not listed, consult your OIDC provider's documentation for a list of claims.

> [!NOTE]
> OIDC providers not listed are compatible with the Profisee platform as long as their claims conform to OIDC standards. Profisee does not currently support SAML-based protocols.

### Azure AD/Entra

|  |  |
| --- | --- |
| Authority URL | https://login.microsoftonline.com/[Your Tenant ID] |
| Client ID | [Your Client ID] |
| Provider Secret | [Your Provider Secret] |
| **Claims Mappings** | |
| User Name | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name |
| User ID | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier |
| First Name | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname |
| Last Name | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname |
| Email  Address | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name |
| Groups | groups |

> [!NOTE]
> Your Azure AD Client ID and Tenant ID are located in the Azure AD web portal under Azure Active Directory > App Registrations . You must update your Azure Application Registration with the optional Groups claim in order to use Groups claims in Profisee. Navigate to your registration, then follow Token configuration > Add groups claim > Select group types to include and select Groups assigned to the application.

### Google

|  |  |
| --- | --- |
| Authority URL | https://accounts.google.com |
| Client ID | [Your Client ID] |
| Provider Secret | [Your Provider Secret] |
| **Claims Mappings** | |
| User Name | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress |
| User ID | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier |
| First Name | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname |
| Last Name | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname |
| Email  Address | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress |
| Groups | groups |

> [!NOTE]
> Your Google Client ID is located in the Google Developer console under Credentials > OAuth 2.0 Client IDs . No Tenant ID is required.

### Okta

|  |  |
| --- | --- |
| Authority URL | https://[Your Tenant ID].okta.com/oauth2/default |
| Client ID | [Your Client ID] |
| Provider Secret | [Your Provider Secret] |
| **Claims Mappings** | |
| User Name | preferred\_username |
| User ID | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier |
| First Name | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname​​​​​ |
| Last Name | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname |
| Email  Address | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress |
| Groups | groups |

Your **Okta Client ID** is located in the [Okta web application](https://www.okta.com/login/) under **Applications**. Your Tenant ID is located under **API** > **Authentication Servers**. Your **Okta Authority URL** is the Issuer URI of the Okta Authorization Server that you are using.

> [!NOTE]
> These claims mappings are for a normal Okta authority URL. If you are using a custom authentification server instead of the default, your claims mappings may vary. Okta groups may require additional configuration. See here for more information on managing security in Profisee using Okta groups.

---