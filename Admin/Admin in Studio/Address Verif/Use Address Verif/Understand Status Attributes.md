# Understand Status Attributes

Address Verification creates several domain-based attributes in the entity selected in the verification strategy. Domain entities for these attributes contain member values used to provide strategy status information. It is important to understand the statuses so that you can interpret verification results, and determine the action that will occur when the strategy runs again. The following tables explain the meaning of these statuses.

## Status Attributes

These attributes identify results of service queries.

The Overall Strategy Status reflects the level of success of all different services across the entire strategy.

| Verification Type | Source Entity | Standard Attribute Name |
| --- | --- | --- |
| Overall Strategy Status | AddressVerificationStatus | strategyName Verification Status |
| Location | LocationVerificationStatus | Location Verification Status |
| Mailing | AddressVerificationStatus | Mailing Verification Status |
| Mailing Geocoding | AddressVerificationStatus | Mailing Geocoding Status |
| Name | AddressVerificationStatus | Name Parsing Status |
| Phone | AddressVerificationStatus | Phone Verification Status |
| Email | AddressVerificationStatus | Email Verification Status |

## Location Verification Status

The Location Verification Status indicates success or failure of location verification.

| Code | Name | Meaning | Reprocessed when processing members of this type: |
| --- | --- | --- | --- |
| 0 | None | Placeholder value (not used) | Unverified members |
| 1 | VerifiedAddress | Successful verification. | All members |
| 2 | VerifiedPlace | Verified city or postal code only. | All members |
| 7 | Verification Failed | Address was not found (appears to be invalid). | All members |
| 8 | Skipped | Not attempted; non-location address detected (such as an overseas military address). | All members |
| 9 | Unsuccessful attempt | The service was unavailable or returned an invalid response. | Unverified members |

A NULL value is also possible for this status. NULL indicates that a member has not yet been processed by the strategy that uses this status field.

## Address Verification Status

The Address Verification Status indicates the level of verification success.

| Code | Name | Meaning | Reprocessed when processing members of this type: |
| --- | --- | --- | --- |
| 0 | None | Placeholder value (not used) | Unverified members |
| 1 | Skipped | Not attempted (as in the case of non-US addresses). | All members |
| 2 | Verified | The address was verified and no corrections were made. | All members |
| 3 | Verified with corrections | The address was verified but corrections were made. | All members |
| 4 | Indeterminate | The address could not be verified but is of a valid format and not known with certainty to be invalid (as in the case of a properly formed email address with a domain that is not verified). | All members |
| 5 | Indeterminate with corrections | The address was verified as indeterminate, and some attributes were corrected. | All members |
| 6 | Verification failed | The address does not appear to be valid. | All members |
| 7 | Verification failed with corrections | The address does not appear to be valid even after some attributes have been corrected. | All members |
| 9 | Unsuccessful attempt | The service was unavailable or returned an invalid response. | Unverified members |
| 10 | License overage | The number of transactions for this type of request has been exceeded. This status applies to Loqate only. | All members |
| 11 | Loqate key has expired | The expiration date for the Loqate license has passed. | All members |
| 12 | Loqate service returned an empty response | The Loqate service returned an empty response. Empty responses indicate that the inputs may not be valid. | All members |

A NULL value is also possible for this status. NULL indicates that a member has not yet been processed by the strategy that uses this status field.