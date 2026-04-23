# Phone Verification Fields

The following fields are available on the Phone tab of an address verification strategy for source and output attributes.

Due to the way cell phone and VoIP companies regulate their data, certain phone data may be inaccurate. In some cases, data will reflect initial settings for the number rather than current information.

| Field | Description |
| --- | --- |
| **Phone Number** | The phone number to verify. Address Verification strips out all special characters, resulting in a ten-digit number. |
| **Area Code** | The original area code from the submitted phone number. If there are not enough digits for the area code, this field is empty. If the area code/prefix combination has split, the new area code is returned by the NewAreaCode field. |
| **New Area Code** | The new area code for the submitted phone number, if the submitted area code has recently undergone a split. An updated area code is a new area code based on the input of an area code/prefix combination that has been split. If no new area code was found, then this field is empty. |
| **Prefix** | The prefix (first three digits after the area code) of the submitted phone number. |
| **Suffix** | The suffix (last four digits) of the submitted phone number. |
| **Extension** | The extension information, if any, of the submitted phone number. |
| **City** | The name of the city associated with the submitted phone number. Because of phone number portability, geographical information may not reflect the true location of the owner of the phone number for wireless and VoIP numbers. |
| **State** | The name of the state associated with the submitted phone number. Because of phone number portability, geographical information may not reflect the true location of the owner of the phone number for wireless and VoIP numbers. |
| **Latitude** | The latitude of the NPA/NXX wire center for the submitted phone number. |
| **Longitude** | The longitude of the NPA/NXX wire center for the submitted phone number. |
| **Country** | The country, either the United States or Canada, associated with the submitted phone number. Because of phone number portability, geographical information may not reflect the true location of the owner of the phone number for wireless and VoIP numbers. |
| **Time Zone** | The time zone associated with the submitted phone number. |
| **Verification Results** | A comma-separated listing of Result Codes for this phone number. |
| **Verification Status** | The overall verification status for this phone number. |