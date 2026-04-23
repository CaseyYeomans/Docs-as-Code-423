# Create an Address Verification Strategy

An address verification strategy defines the context of operation (the source entity in the system model), source data attributes, output attributes, and behaviors of the verification process. An Address Verification Administrator must create a strategy before users can perform address verification for a given entity. Metadata must be created by a System Administrator.

Keys must be applied before beginning this procedure. Without keys, New will be enabled in the Strategy tab, but Options will be greyed out. Refer to the Adding service provider keys section for details.

All users that need to process address verification strategies must have permission to use address verification. For more information, see [Select users to access Address Services](https://support.profisee.com/wikis/profiseeplatform/select_users_to_access_address_services).

1. In the navigation panel, click **Administration**.
2. Under Administration, click **Address Verification**.

The **Address Verification** tab appears.
3. Click **New**.

The address verification definition pane opens.
4. Complete the strategy definition based on your model structure.

## Address Verification Toolbar

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i9c5c6421ccdf697f.png)

Use the following options on the toolbar in the Address Verification tab to manage, view, and create address verification strategies.

- **New**: Create a new address strategy
- **Copy**: Duplicate an existing address strategy
- **Edit**: Edit an existing address strategy
- **Delete**: Remove an address strategy
- **Import/Export**: Save and import address strategy files for portability between systems and for backup purposes
- **Process**: Use an address strategy to verify member data
- **View**: View the results report, relevant entity, processing status for a selected strategy, operational status of the verification services, and transaction usage details

## Configuring Your Strategy Options

The options for configuring a verification strategy are organized within tabs (Strategy, Criteria, Location, Mailing, Name, Email, Phone, Processing). You can create a strategy to verify any combination of information relating to these tabs, depending on your verification service licenses. Tabs containing unlicensed services will not be available for use. The contents of each tab are described in detail in their respective topics.

- [Configure Settings in the Strategy Tab](https://support.profisee.com/wikis/profiseeplatform/configure_address_settings_on_the_strategy_tab)
- [Configure Settings in the Criteria Tab](https://support.profisee.com/wikis/profiseeplatform/configure_settings_on_the_criteria_tab_in_address_verification)
- [Configure Settings in the Location Tab](https://support.profisee.com/wikis/profiseeplatform/configure_settings_on_the_location_tab)
- [Configure Settings in the Mailing Tab](https://support.profisee.com/wikis/profiseeplatform/mailing_verification_fields)
- [Configure Settings in the Name Tab](https://support.profisee.com/wikis/profiseeplatform/configure_settings_on_the_name_tab)
- [Configure Settings in the Email Tab](https://support.profisee.com/wikis/profiseeplatform/configure_settings_on_the_email_tab)
- [Configure Settings in the Phone Tab](https://support.profisee.com/wikis/profiseeplatform/configure_settings_on_the_phone_tab)
- [Configure Settings in the Processing Tab](https://support.profisee.com/wikis/profiseeplatform/configuring_settings_on_the_processing_tab)

Only users with the System Administrator and Address Verification Administrator roles can configure Address Verification strategies.

When you delete an address verification strategy, or cancel creating one before you have saved it, the attributes created as part of that strategy remain in the entity. If you prefer, you can delete these items manually after deleting the strategy.

The location service cannot verify military addresses. Avoid mapping location output data as mailing input data for these addresses, because there will be no data to verify.