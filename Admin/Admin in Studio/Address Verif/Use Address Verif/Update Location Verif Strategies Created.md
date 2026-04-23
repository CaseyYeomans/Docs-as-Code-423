# Update Location Verification Strategies Created Prior to Maestro  4.0.3

In Maestro 4.0.3, a significant change occurred with respect to address verification licensing. Instead of using the Bing location verification service provided through Profisee, customers began choosing their own location verification provider (either Bing or Google) and entering their own license keys.

You can continue using address verification strategies created prior to 4.0.3 with Profisee Platform. If you choose to switch location verification service providers, you will need to update and re-save your strategies after you import strategies containing location verification, or after upgrading your database containing the strategies.

- If you choose Bing as your location verification service provider, then it is not necessary to update anything. You can use your old strategies as they are.
- If you have selected Google as your location verification service provider, do the following after applying your Google API key:

1. Open each address verification strategy that includes location verification.
2. On the Location tab, select an output attribute for Street Number.

Google verification responses include Street Number as a separate field, which must be mapped to a separate attribute.
3. Select **Prepend Street Number** as the Output Format for Street Address.
4. Save and close the strategy.

If you no longer need to include location verification in a strategy, to do the following:

5. Open each strategy containing location verification.
6. Clear the Location check box on the Strategy tab.

Location verification is not required for mailing verification in version 4.0.3 and later.

7. Make sure that the country of the address is identified as an input to mailing verification by doing one of the following:
1. Select a Country or Region source attribute on the Mailing tab,

**--or--**

1. If all of the records are assumed to be from the same country, click **Options** on the Mailing tab and select a default country.

8. Save and close the strategy.