# Obtain a Bing or Google Location Verification Service Provider Key

To use location verification with Address Verification, you must first obtain a key from a location service provider. You can use a key obtained from either Google Maps or Bing Maps. The following procedures explain how to get a low-volume transaction key at no charge. Carefully review the licensing agreements on the respective sites for the Bing or Google key you select to use with Address Verification.

The specific steps required to obtain a key are subject to change without notice. If you have issues with obtaining a key, contact [Profisee support](https://profisee.desk.com/).

For best results, perform the following procedure using the Chrome browser.

## To Obtain a Key from Google Maps:

1. Go to [console.developers.google.com](http://console.developers.google.com/ "console.developers.google.com") and create an account, if necessary.
2. Under Google Maps APIs, click **Google Maps Geocoding API**.
3. Under API Manager, on the left side of the page, click **Credentials**.
4. In the Credentials pane, click **Create a project**.
5. Complete the project options, and then click **Create**.
6. Select API key from the list.
7. In the **API key created** pop-up, click **Restrict key**.
8. Enter a name for the new server key in the **Name** field.
9. Select the method you want to use to restrict the key.

For the purposes of verification strategies, it is most likely you will want to restrict the key by **HTTP referrers** or **IP addresses**.
10. Click **Create**.
11. Copy the key that displays and save it. This is the key you will use with Address Verification.

This type of key is available at no charge and offers a limited number of transactions. Be sure you review the terms, details of monitoring, and any limits on the number of transactions on [the Google site](https://support.google.com/cloud/answer/6158862?hl=en#creating-server-api-keys).

To get a premium key with fewer restrictions, refer to the [documentation for premium keys](https://developers.google.com/maps/documentation/geocoding/get-api-key#premium-auth) on the Google site.

Refer to Google's [instructions](https://support.google.com/cloud/answer/6310037) for keeping your key secure.

After you have obtained your Google Maps key, add it to [Profisee System Settings](https://support.profisee.com/wikis/profiseeplatform/configure_bing_or_google_location_verification_system_settings).

## To Obtain a Key from Bing Maps:

1. Go to <https://www.bingmapsportal.com> and create an account.
2. Sign in to your account if you are not already signed in.
3. Click **My account**, and then click **My Keys** from the list.
4. In the Application name field, enter **Profisee**.
5. Leave the Application URL field blank.
6. Under Key type, select **Basic**.

A Basic key is available at no charge and allows a limited number of transactions per calendar year. Check the terms of the basic key license to determine whether you need an Enterprise key instead at [Bing Maps](https://www.microsoft.com/maps/licensing/options.aspx).

7. Under Application type, select **Universal Windows App**.
8. Click **Create**.

After you have obtained your Bing Maps key, add it to [Profisee System Settings](https://support.profisee.com/wikis/profiseeplatform/configure_bing_or_google_location_verification_system_settings).