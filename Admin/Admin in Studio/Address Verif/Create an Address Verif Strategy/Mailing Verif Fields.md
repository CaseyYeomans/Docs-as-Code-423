# Mailing Verification Fields

The mailing address verification service verifies mailing addresses in purchased geographical coverage areas. The following fields on the Mailing tab of an address verification strategy apply to source and output attributes for Melissa Data and Loqate. You can either assign these fields to entity attributes manually, or use the Attribute Assistant to complete the task more quickly.

The following table includes a comprehensive list of all possible fields. A subset of the fields in the table is available on the Mailing tab of an address verification strategy for source and output attributes. The actual available fields are dependent upon your license.

| Field | Description | Type |
| --- | --- | --- |
| **Address Line 1** | The street address. Any suite or secondary address information in the Address Line 1 input is moved to the Suite or PrivateMailBox field. | Input and Output |
| **Address Line 2** | The secondary street address. Any suite or secondary address information in the Address Line 2 input is moved to the Suite or PrivateMailBox field. | Input and Output |
| **Address Lines 3 through 8** | Additional address fields available for street addresses information. | Input and Output |
| **Address Lines 9 through 12** | Additional address fields available for street addresses information. | Output |
| **City/Locality** | The city, locality, or municipality. | Input and Output |
| **Dependent Locality** | A smaller population center data element dependent on the City/Locality value. | Output |
| **Double Dependent Locality** | The smallest population center element, dependent on both the City/Locality and Dependent Locality values. | Output |
| **Super Admin Area** | The largest geographic data element within a country. | Output |
| **State** | The state or province. | Input and Output |
| **Sub Admin Area** | The smallest geographic data element within a country. | Output |
| **Postal Code/ZIP** | The ZIP Code or postal code for the address. | Input and Output |
| **Country/Region** | The country in which the address is located. Note that when using Loqate, the country name must be spelled out in its entirety. See [here](https://support.profisee.com/wikis/profiseeplatform/international_address_verification_regions_and_codes) for a list of accepted country names. | Input and Output |
| **Country Code - 2 Char** | The ISO 3166 two-character country code. | Output |
| **Country Code - 3 Char** | The ISO 3166 three-character country code. | Output |
| **Country Code - 3 Digit** | The ISO 3166 three-digit numeric country code. | Output |
| **Building Name** | The name of an individual location. | Output |
| **Plus4/Secondary Postal Code** | For a U.S. address, the Plus4 is the four-digit portion of the ZIP + 4 for the address. | Output |
| **Suite** | Optional input containing the suite name and number. Use this field to send the suite number if that information is stored separately from the street address in your original data. The suite information will also be detected if it is part of the AddressLine1 field or stored in AddressLine2. Use this field if your source data has an explicit Suite attribute of its own. The suite may be output using Suite Number or Suite Name or by using the Output Format options in Address Line 1 or Address Line 2. | Input |
| **Company Name** | Used when validating corporate addresses. | Input and Output |
| **Last Name** | Provided as input only. Used when validating personal addresses. | Input |
| **Street Number** | The street number portion of the street address. If the street address is 123 North Main Street, this field returns 123. | Output |
| **Street Name** | The name portion of the street address. If the street address is 123 North Main Street, this field returns Main. | Output |
| **Street Prefix** | The prefix portion of the street address. If the street address is 123 North Main Street, this field returns North. | Output |
| **Street Suffix** | The name portion of the street address. If the street address is 123 North Main Street, this field returns St. | Output |
| **Pre Direction** | The pre-directional portions of the street address only. If the street address is 123 North Main Street, the Pre Direction field returns N. | Output |
| **Post Direction** | The post-directional portions of the street address only. If the address is 456 Maple Street West, the Post Direction field returns W. | Output |
| **Dependent Street** | The dependent street or block. | Output |
| **Suite Number** | The standardized suite number for the current address. If the street address is 123 North Main Street #B, the Suite Number field returns B. | Output |
| **Suite Name** | The standardized suite name for the current address. If the street address is 123 North Main Street Apt. B, the Suite Name field returns Apt. | Output |
| **Private Mailbox Number** | The parsed private mailbox (PMB) number from an address for a Commercial Mail Receiving Agency (CMRA) such as the UPS Store. These are often located at shopping centers and the store itself often has a suite number as well as a PMB number. For example, for 1234 Main Street, Suite C1 PMB#101, the PMB number is 101. | Output |
| **Private Mailbox Name** | The parsed private mailbox (PMB) name from a street address that belongs to a Commercial Mail Receiving Agency (CMRA) such as the UPS Store. These are often located at shopping centers and the store itself often has a suite number as well as a PMB number. The name field contains either # or PMB. | Output |
| **Carrier Route** | The four-character code defining the carrier route for that record. The first character of this property is always alphabetic, and the last three characters are numeric. | Output |
| **Delivery Point Code** | The tenth and eleventh digits of the POSTNet barcode number. The complete twelve-digit POSTNet barcode number consists of the ZIP + 4, minus any dash, the two-digit DeliveryPointCode and the single-digit DeliveryPointCheckDigit. | Output |
| **Delivery Point Check Digit** | The twelfth digit of the POSTNet barcode number. | Output |
| **Address Type** | A single-letter code for the delivery location. For US addresses: A: Alias F: Firm (single business or organization) G: General Delivery (general mail pickup) H: High-rise (business park, plaza) P: PO Box R: Rural Route/Highway S: Street/Residential Address For Canadian addresses: 1: Street 2: Street Served by Route and GD 3: Lock Box 4: Route Service 5: General Delivery B: LVR Street C: Government Street D: LVR Lock Box E: Government Lock Box L: LVR General Delivery K: Building | Output |
| **ZIP Type** | A single-character code identifying the ZIP Code type. Can have the following values: U: Military/APO P: PO Box U: Unique (assigned to specific organizations) Blank: Standard | Output |
| **Address Key** | A required output from mailing verification used as an input for Melissa Data geocoding requests. | Output |
| **Verification Results** | A comma-separated listing of Result Codes for this address. | Output |
| **Verification Status** | The overall verification status for this address. | Output |
| **Latitude (Geocoding)** | The latitude of the address. Latitude is comprised of the geographic coordinates of a point measured in degrees north or south of the equator. | Output |
| **Longitude (Geocoding)** | The longitude of the address. Longitude is comprised of the geographic coordinates of a point measured in degrees east or west of the Greenwich meridian. | Output |
| **Census Block (Geocoding)** | The Census Block code for the address. | Output |
| **Census Tract (Geocoding)** | The four- or six-digit Census Bureau Census Tract code for the address. | Output |
| **County Name (Geocoding)** | The name of the county where the address is located. | Output |
| **County FIPS (Geocoding)** | The five-digit Federal Information Processing Standard (FIPS) code for the county where the address is located. The first two digits are the state code and the last three indicate the county within the state. | Output |
| **Place Code (Geocoding)** | The Census Bureau Place Code for the address. The ZIP Code may place a location within one city even though it is physically located within a neighboring area. Place Code and Name are returned. | Output |
| **Place Name (Geocoding)** | The Census Bureau Place Name for the input address. The ZIP Code may place a location within one city even though it is physically located within a neighboring area. Place Code and Name are returned. | Output |
| **Time Zone Code (Geocoding)** | The one- or two-digit code for the time zone where the input address is located. | Output |
| **Time Zone Name (Geocoding)** | The name of the time zone where the input address is located. | Output |
| **CBSA Code (Geocoding)** | Five-digit code for the specific Core Based Statistical Area (CBSA) for the input address. | Output |
| **CBSA Title (Geocoding)** | The Census Bureau name or official title for the CBSA of the input address. | Output |
| **CBSA Level (Geocoding)** | The CBSA level (either metropolitan or micropolitan) for the input address. | Output |
| **CBSA Division Code (Geocoding)** | A five-digit code for the CBSA division, if one exists, for the input address, A value only exists when the CBSA is broken into divisions. | Output |
| **CBSA Division Title (Geocoding)** | The name of the CBSA division, if one exists, for the input address. A value only exists when the CBSA is broken into divisions. | Output |
| **CBSA Division Level (Geocoding)** | The CBSA level (either metropolitan or micropolitan), if one exists, for the input address. | Output |
| **Mailing Geocoding Results (Geocoding)** | A comma-separated listing of geocoding result codes for this address. | Output |
| **Mailing Geocoding Status (Geocoding)** | The overall geocoding verification status for this address. | Output |