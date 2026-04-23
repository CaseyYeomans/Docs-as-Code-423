# Configure Address Settings on the Strategy Tab

Configure the basic settings that define your address verification strategy on the Strategy tab.

1. In the **Name** field, enter a name for the strategy.
2. From the **Entity** list, select the entity in the system model that contains the address attributes to verify.

Only the entities where the user has Administration permission display in the list.

3. From the **Verification status attribute** list, select an existing attribute to hold the status, or create a new attribute by selecting **Create New**.

This attribute contains the overall status of the verification strategy for each member.
4. From the following options, select one or more verification types.

Each option you select to verify has a corresponding tab requiring configuration. For example, if you select the Location Verification option, you must also complete the verification options on the Location tab. Available types depend upon your service license information.

- **Location Verification**: Verifies the physical location of an address, completing partial addresses and including geocoding information. For more information, see [Configure Settings in the Location Tab](https://support.profisee.com/wikis/profiseeplatform/configure_settings_on_the_location_tab).

Under **Source Type**:

- Select **Separate Fields** if your source address data spans multiple attributes.
- Select **Single Field** if your source address is contained in a single attribute.
- **Mailing Verification**: Standardizes and verifies US and Canada postal addresses based on standards set by the United States Postal Service and Canadian Post, or standardizes and verifies mailing addresses in select regions worldwide (depending on your license). For more information, see [Configure Settings in the Mailing Tab](https://support.profisee.com/wikis/profiseeplatform/configuring_settings_on_the_mailing_tab) and [Mailing Verification Fields](https://support.profisee.com/wikis/profiseeplatform/mailing_verification_fields).
- **Name Parsing**: Standardizes and verifies name format and verifies gender. For more information, see [Configure Settings in the Name Tab](https://support.profisee.com/wikis/profiseeplatform/configure_settings_on_the_name_tab) and [Name Verification Options](https://support.profisee.com/wikis/profiseeplatform/name_verification_fields).
- **Email Verification**: Verifies email addresses. For more information, see [Configure Settings in the Email Tab](https://support.profisee.com/wikis/profiseeplatform/configure_settings_on_the_email_tab) and [Email verification Fields](https://support.profisee.com/wikis/profiseeplatform/email_verification_fields).
- **Phone Verification**: Verifies phone numbers. For more information, see [Configure Settings in the Phone Tab](https://support.profisee.com/wikis/profiseeplatform/configure_settings_on_the_phone_tab) and [Phone verification Fields](https://support.profisee.com/wikis/profiseeplatform/phone_verification_fields).

You must complete information on this tab before entering other address verification options. Because the other options for configuring the rest of the strategy are context-based, the basic reference information on this tab is required before you can continue.