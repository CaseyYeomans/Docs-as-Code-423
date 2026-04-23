# Process Address Verification in Batch Mode

When an address verification strategy is processed in batch mode, the processing server for the strategy issues a request for each address that will be validated. The processing server receives a response back with zero, one, or multiple possible addresses, each with a confidence level indicating how likely it is to be a match.

To process an address verification strategy in batch mode:

1. In the navigation panel, click **Administration**.
2. Click **Address Verification**.
3. Select an address strategy from the list.
4. On the Address Verification toolbar, click **Process**, and then click **Process** on the menu.
5. In the Process Address Verification Status dialog, select the model version you want to run address verification against from the **Version** list.
6. Select the members to include in the verification process. You can process:

- **Unverified members**: Processes members without a verification status
- **Unverified and changed members**: Processes members without a verification status and members that have changed since the last time verification processed
- **All members**: Processes all members regardless of verification status
7. Select the type of verification to perform. You can select any combination of:

The verification strategy must be configured to support your verification selections.

- **Location Verification**
- **Email Verification**
- **Mailing Verification**
- **Phone Verification**
- **Name Parsing**

8. Click **Start**. The Address Verification status window opens. Use this window to monitor the processing status. The strategy will continue to process if you close the window.

The Confidence Threshold setting on the Location tab specified in the attribute verification strategy determines if the output standard address attributes are populated when multiple possible addresses returned. For example, if the confidence threshold is set to **High**, then addresses returned with a Medium or lower confidence level are not used to update the standard address fields.

The Confidence output attribute is populated with the confidence level. Use this value to filter records manually and select the appropriate address.