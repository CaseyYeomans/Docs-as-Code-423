# Location Verification Fields

The Location tab of an address verification strategy includes the location verification input and output fields shown in the table which follows. These fields appear as attributes in the entity used in the address verification strategy. Assign the attributes manually, or use the Attribute Assistant to automatically create them.

If you have also licensed mailing verification, you can process the data first using location verification, and then run mailing verification with the location data as input.

A subset of the following fields is available on the Location tab of an address verification strategy for source and output attributes. Actual available fields are dependent upon your license.

| Field | Description | Type |
| --- | --- | --- |
| **Single Field** | The entire address in a single field. | Output |
| **Address Line 1** | The street address. Any suite or secondary address information in the Address Line 1 input is moved to the Suite or PrivateMailBox field. | Input |
| **Address Line 2** | The secondary street address. Any suite or secondary address information in the Address Line 2 input is moved to the Suite or PrivateMailBox field. | Input |
| **Address Line 3** | Additional address field available for street addresses information. | Input |
| **Street Address** | Output containing the street number and street name. | Output |
| **City/Locality** | The city or municipality. | Input and Output |
| **State/Admin Area** | The state or province. | Input and Output |
| **Postal Code/ZIP** | The five-digit ZIP Code or postal code for the address. | Input and Output |
| **Country/Region** | The country in which the address is located. | Input and Output |
| **Country Code - 2 Char** | The ISO2 country code. | Output |
| **County** | The name of the county. | Input and Output |
| **Latitude** | The latitude of the verified location. | Output |
| **Longitude** | The longitude of the verified location. | Output |
| **Confidence** | The score indicating the confidence score for the verified location. | Output |
| **Location Response Count** | The number of possible addresses returned for the parsed location. | Output |
| **Status** | The location verification status. | Output |
| **Street Number** | The street number portion of the street address. If the street address is 123 North Main Street, this field returns 123. | Output |