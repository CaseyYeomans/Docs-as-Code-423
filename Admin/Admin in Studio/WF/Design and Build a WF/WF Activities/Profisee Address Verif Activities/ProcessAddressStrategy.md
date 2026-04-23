# ProcessAddressStrategy

The ProcessAddressStrategy activity allows a designer to build a workflow that verifies an address using the supplied StrategyName.

| | | |
| --- | --- | --- |
| **ProcessAddressStrategy In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| MembersToInclude\* | AddressProcessingMembersToIncludeType | Identifies the status of members in the entity to process. |
| StrategyName\* | String | The strategy name to use to apply the match. This allows the workflow to dynamically adjust the strategy based on information the activity has at runtime. |
| ProcessServiceTypes\* | Collection<ExternalServiceType> | The maximum time to wait for a response in case another process has the matching index locked. |
| **ProcessAddressStrategy Out Arguments** | | |
| OperationResult | MaestroOperationResult | Indicates the results of the strategy execution. |

*\*Argument is required*

### Remarks

Processing an address strategy with this activity is an asynchronous request. The activity does not wait for the strategy to fully process before continuing.

**Options for AddressProcessingMembersToIncludeType:**

- UnverifiedMembers
- UnverifiedAndChangedMembers
- AllMembers

**Options for ProcessingServicesTypes:**

- LocationVerification
- MailingAddressVerification
- NameParsing
- EmailVerification
- PhoneVerification
- MailingAddressVerificationInternational
- LocationVerificationGoogle
- MelissaDataGeocode

###