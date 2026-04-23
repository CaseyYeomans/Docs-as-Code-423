# VerifyRecordAddress

The VerifyMemberAddress activity allows a designer to invoke address verification for a given member within a workflow.

| | | |
| --- | --- | --- |
| **VerifyMemberAddress In Arguments** | | |
| **Argument Name** | **Data Type** | **Description** |
| MemberDataContext\* | [MemberDataContext](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type) | Identifies the member and entity that is subject to verification |
| ProcessServiceTypes\* | Collection<ExternalServiceType> | Identifies the types of processing to run on the specified member |
| **VerifyMemberAddress Out Arguments** | | |
| Results | Collection<Member> | A Collection of members with address verified |
| OperationResult | MaestroOperationResult | Identifies the success or failure of the operation |
| Errors | Collection<Error> | Identifies any service errors that may have occurred during the processing of the request |

*\*Argument is required*

### Remarks

If workflow configuration is missing the address strategy, workflow instance will be suspended.

**Option for ExternalServiceType:**

- LocationVerification
- MailingAddressVerification
- NameParsing
- EmailVerification
- PhoneVerification
- MailingAddressVerificationInternational
- LocationVerificationGoogle
- MelissaDataGeocode

### See Also

- [Process Address Strategy](https://support.profisee.com/wikis/profiseeplatform/process_address_strategy)
- [MemberDataContext](https://support.profisee.com/wikis/profiseeplatform/memberdatacontext_type)