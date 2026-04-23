# Troubleshoot Address Verification

**Issue**: All addresses display a verification status of **Skipped** when verified through the grid or with batch processing.

- Use the View menu on the Address Verification tab to check that the services are up and running.
- Make sure you can access the address verification services using a browser.
- Check your firewall for rules that could block address verification requests (both outgoing and incoming).

**Issue**: There are many skipped addresses when performing batch processing.

- If the skipped addresses are primarily outside of North America, check your available number of international transactions to make sure that you have not run out. For more information, see [Tracking international mailing address verification usage](https://support.profisee.com/wikis/profiseeplatform/track_international_mailing_address_verification_usage).
- Verify one of the skipped addresses from the entity grid to see more detailed information returned by the verification service.
- If there is no populated country attribute value for the skipped address, make sure that the Default Country is set for the strategy. For more information, see [Configuring settings on the Mailing tab](https://support.profisee.com/wikis/profiseeplatform/configuring_settings_on_the_mailing_tab).

**Issue**: After attempting to perform location verification, many locations known to be valid have a Lookup Status of "Unsuccessful Attempt."

- Increase the value for the Location verification maximum call rate setting in System Settings.For more information, see [Configuring location verification System Settings in Profisee](https://support.profisee.com/wikis/profiseeplatform/configure_bing_or_google_location_verification_system_settings).

**Issue**: After entering a new location verification provider license key in System Settings, you are unable to verify addresses.

- Open and re-save your address verification strategies that include location verification.
- Open the Address Verification View menu and select Operational Statuses of Services. Make sure that the service provider is listed as Operational. If it is not, check your key to make sure you pasted it correctly.

**Issue**: After adding or changing a license key (for Bing, Google, Melissa Data, or Loqate) in System Settings, unusual errors occur when attempting to edit or process address verification strategies.

- Reconnect to , and inform all attached users that they should reconnect as well. Changing or adding verification service keys under System Settings alters the server license information. Reconnecting allows the new license information to be applied.

**Issue**: When attempting to process a verification strategy in batch mode, all of the verification types are grayed out.

- Address Verification has expired. Contact Profisee for information on renewing your license.