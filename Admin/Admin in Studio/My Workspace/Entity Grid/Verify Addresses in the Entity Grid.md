# Verify Addresses in the Entity Grid

You can validate addresses for individual members, or select multiple members and validate them in a batch. If you select an individual member, you can review the result of the address lookup and select the appropriate address if multiple addresses are returned.

## Verify the Address for a Single Member

1. From an entity view tab, select a grid member for verification.
2. Right-click the member and then click **Verify Address** on the menu.
3. If more than one address verification strategy is available, select the desired strategy and click **Next**. If only one strategy is available, you will not be prompted.
4. If more than one address is returned, select the Output row with the correct address. If only one address is returned, or if location verification was not included in this strategy, this window does not display. Continue to the next step.

When multiple possible addresses are returned for a single member, the Source address displays in the first row with the Output addresses returned from the address service below it. In addition, the confidence level of the address displays. This applies to information returned by the location verification service only.
5. Review address verification results.

The results returned from the verification services display in a tabbed window. Each tab in the window correlates to a tab within the address verification strategy and contains the results based on the strategy configuration. A **green checkmark** on a tab indicates that this portion of the address verification strategy processed successfully. A **red exclamation point** means that there were issues with verifying the input data for this portion of the strategy. Refer to the Result Codes on each tab for additional information. Fields shaded green indicate information returned that differs from the input information.
6. Click **Finish**.

The output address attributes appear in the entity grid. Publish the data to Profisee to update the member information.

## Verify Addresses for Multiple Members

1. From an entity view tab, click the row headers to select individual members, or click the top of the row header column to mark all rows based on your current page size setting.
2. Right-click inside the row for one of the selected members, select Verify Address on the menu.
3. If more than one address verification strategy is available, select the strategy to you want to use and then click Next. If only one strategy is available, continue to the next step.
4. Click **OK** to acknowledge the message stating that address verification is in progress.

The verification process runs in a batch mode.

5. Click **Refresh** on the main toolbar to monitor progress. You can view the results in the entity grid as the members are populated in the output address attribute columns in the entity grid.

In this mode, Profisee does not present the results of the lookup as it does with a single member lookup. Instead, it uses the Confidence Threshold setting on the strategy Location tab to determine if the output standard address attributes are populated when multiple possible addresses are returned. For example, if the confidence threshold is set to "High," then addresses returned with a Medium or lower confidence level will be discarded. The address lookup status attribute will be populated with the confidence so you can filter on those records and manually verify those addresses in the entity grid in order to select the appropriate address returned by location services.

The source address attributes and output address attributes that contain the results of the address lookup are defined in the address verification strategy. An address verification strategy must be created before addresses can be verified.

## See Also

[Create an Address Verification Strategy](https://support.profisee.com/wikis/profiseeplatform/create_an_address_verification_strategy)

[Select Users to Access Address Services](https://support.profisee.com/wikis/profiseeplatform/select_users_to_access_address_services)