# Configure Bing or Google Location Verification System Settings

To use location verification in your address verification strategies, you must include a location services license in System Settings. You can choose to [purchase a license from either Bing or Google](https://support.profisee.com/wikis/profiseeplatform/obtain_a_bing_or_google_location_verification_service_provider_key). This license determines the service that will verify your address information when you submit it for verification using a strategy that includes location verification.

After you have obtained your license key, you must add it to System Settings in order to use the service in verification strategies.

To add your license key:

1. Click **Settings** in the main toolbar.
2. Click **System Settings**.
3. Locate the **Service Provider Keys** category.
4. Copy (CTRL+C) your license key from Bing or Google to the clipboard.
5. Do one of the following:

**--or--**

- For Bing licenses: Locate the **Bing API Key** row, and then paste (CTRL+V) the key in the **Value** column.
- For Google licenses: Locate the **Google API Key** row, and then paste (CTRL+V) the key in the **Value** column.
6. Locate the **Location verification maximum call rate** setting in System Settings (under the Address Verification category).
7. Enter a number (in maximum API calls allowed per minute) to prevent sending location verification requests too quickly.

Check with your location verification service provider to determine the value you should enter for this setting.

Location verification service providers may require that users limit their requests per minute. The Location verification maximum call rate prevents your system from exceeding this limit and causing the service provided to disable your key.

Regardless of the speed of your connection or the number of cores available on your server, location verification will be limited to this rate.

If you are using a location verification key that you obtained through Profisee (included in your license file) then this setting is ignored, and the rate is controlled by your license file.

8. Click **Save** or **Save and Close**.
9. Reestablish your connection.

The administrator and all attached users should reconnect after a new key is added. Adding and updating keys affects licensing information, and reconnecting applies the new license settings.

If you include a key in both the Bing API Key and the Google API Key fields, then Address Verification will use the Google key by default.