# Log In to the Profisee Platform

Once Profisee FastApp Studio has been installed, you must log in before you can begin administering the solution. The login process allows users to log in to Profisee using one or more configured authentication providers. If only one authentication provider is configured, the user will be automatically redirected to that authentication provider. If more than one authentication provider is configured, the user will be able to select which one to use for authentication. When Windows Active Directory is chosen as the authentication provider, the user will automatically be logged in using the credentials they are running the application under.

1. Click **Login**.
*The login window will automatically prompt you to log in once you launch FastApp Studio. If this window is closed or does not appear, you can manually log in by clicking the **Login** button on the top-left corner of the window.*![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i4683f87600b896e2.png)
2. If more than one authentication provider is configured, select a provider to redirect to. If only one authentication provider is configured, you will be automatically redirected.
3. Sign-in to the authentication provider.

The available providers will vary per environment based on the authentication providers [configured by your system administrator](https://support.profisee.com/wikis/profiseeplatform/configuration_manager_new_installation). If only one provider has been configured, you will be automatically redirected to that provider and will not need to select a provider to continue.

- **Using Windows Active Directory**: Depending on your browser configuration, you may be prompted to enter your username and password. If so, enter the credentials associated with your Profisee account and submit. To automatically sign in without entering your credentials, you must [set the authentication page as a trusted web site](https://effortz.com/add-website-browsers-trusted-sites-windows-os/) in your default browser. Once this is set as a trusted site, you will automatically log in using the credentials you previously used to log in. Depending on your organization's policies, you may need to work with your system administrator to configure a trusted web site.
- **From Azure Active Directory**: When logging in from Azure Active Directory, you will be redirected to the Azure Active Directory login page. The authentication experience will be determined by your organization's configuration of Azure Active Directory, which may include multi-factor authentication.
- **From Other Authentication Service**: When logging in from other OpenIDConnect authentication providers, you will be redirected to that provider's login page. The authentication experience will be determined by your organization's configuration of that provider, which may include multi-factor authentication.

Once successfully authenticated, you will be redirected to a confirmation screen. You have successfully logged in and can navigate back to FastApp Studio.

You cannot log into the Profisee platform until a system administrator adds you as a user. If you cannot log into the platform after successful authentication, contact your system administrator.