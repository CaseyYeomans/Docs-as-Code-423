# Address Verification Overview

Address Verification provides the ability to create strategies for a variety of data types. To process strategies and receive results, you must obtain licenses for individual verification services through the applicable verification service providers.

Five types of data verification services are available:

- Location
- Mailing
- Name
- Email
- Phone

You can verify location and contact information stored in any entity in your Profisee database. For example, if you have an entity that contains customer Address Line1, City, State/Province and Postal Code attributes, you can configure a strategy to look up addresses and then return the corrected or verified address after checking with an online verification service.

Be sure to create separate attributes to hold the results of the verification process instead of replacing values in the source attributes in the entity. The Address Verification feature can create these output attributes for you automatically as a part of the strategy configuration step.

## Location

Location verification, using your Bing or Google key, provides information for near-global coverage of physical addresses. It can provide some or all of the following enhancements for address data, depending on the information available:

- **Verification**: Is this a valid address?
- **Completion**: What is the standardized format for this address?

Can correct and complete physical addresses.
- **Geocoding**: Where is this address?

Can add latitude and longitude, counties, countries, full postal codes and missing address information.

Location verification can improve poorly formed addresses, or find multiple possible alternative addresses. This verification type is most useful to organizations requiring consistent address information to get better matching results.

Organizations requiring address information for marketing or billing purposes, or to contact individuals and organizations, should consider using mailing verification in addition to location verification.

## Mailing

Mailing verification is accomplished using your Profisee license for Melissa Data or Loqate (or both), and is most useful for organizations where address accuracy and the ability to deliver items to a physical address is important. Use mailing verification when the postal address will be used to contact individuals or organizations.

Address Verification supports two mailing verification service providers: Melissa Data and Loqate.

Melissa Data lets you verify addresses for the US and Canada geographical regions. The mailing verification service standardizes and verifies postal mailing addresses based on standards set by the United States Postal Service and the Canadian Post. The service attempts to find a single address match, or no match at all. In addition, Melissa Data can provide geocoding information for the US and Canada through a mailing verification strategy.

Loqate offers verification on a per-transaction basis for international mailing addresses. Loqate provides parsing, verification, and standardization of mailing addresses worldwide.

## Name

Name verification verifies and parses full name fields into individual name components and spousal (such as husband and wife) components for the US and Canada. Provided through Melissa Data.

## Email

Email verification parses and verifies email addresses for the US and Canada. Provided through Melissa Data.

## Phone

Phone verification parses and verifies phone numbers for the US and Canada. Provided through Melissa Data.

## How it Works

Administrators configure one or more verification services and configure verification strategies. They identify users that are allowed to access the verification services, and then these end users interactively use the strategies through the entity grid to verify and correct addresses.

Administrators can also verify and correct addresses in a server batch mode.

To implement a data verification process:

1. Add your verification service provider license keys to System Settings > Service Provider Keys.

For more information, see [Configure Bing or Google location verification System Settings](https://support.profisee.com/wikis/profiseeplatform/configure_bing_or_google_location_verification_system_settings) and [Add your Loqate key](https://support.profisee.com/wikis/profiseeplatform/add_your_loqate_key).
2. Create a verification strategy based on your model structure.

For more information, see [Create an address verification strategy](https://support.profisee.com/wikis/profiseeplatform/create_an_address_verification_strategy).
3. Assign access to specific users to allow them to process verification strategies.

For more information, see [Select users to access Address Services](https://support.profisee.com/wikis/profiseeplatform/select_users_to_access_address_services).
4. Process the address strategy in either batch mode or for selected members in the entity grid.

For more information, see [Process address verification in batch mode](https://support.profisee.com/wikis/profiseeplatform/process_address_verification_in_batch_mode) and [Verifying addresses in the entity grid](https://support.profisee.com/wikis/profiseeplatform/verify_addresses_in_the_entity_grid).

When you delete a verification strategy, the attributes created as part of that strategy remain in the entity. If you prefer, you can delete these items manually.

The location service cannot verify military addresses. Avoid mapping location output data as mailing input data for these addresses because there will be no data to verify.

### Academy Preview

The following content is from the Profisee Academy course on Address Verification. Academy customers can see the full course [here](https://support.profisee.com/lms/courseinfo?id=00u00000000004o00aM).