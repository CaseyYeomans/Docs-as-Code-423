# Updating Portal Themes using the REST API

The REST API allows users with sufficient permissions to change the color values for various elements of the Profisee Portal. To do so, scroll down the Swagger page to locate the **Themes** section of the API.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i53798948c338a452.png)

Here, you can use the above GET requests to view the existing RGB values for existing portal elements. You can also edit these RGB values by using the above PUT requests.

The changeable elements and the default values for these elements are as follows:

| | | |
| --- | --- | --- |
| **Element Name** | **Default Values** | **Areas Impacted** |
| **bannerPrimary** | 255, 255, 255 | Form container backgrounds, governance dialog background, matching control container backgrounds |
| **bannerFi** | 27, 49, 65 | Menu item hover format |
| **bannerSecondary** | 0, 250, 221 | Form tabs, portal input fields |
| **contentPrimaryBg** | 255, 255, 255 | Entity grid column heading background, form input field background, matching control |
| **contentPrimaryFi** | 107, 114, 128 | Flyout menu and grid row content, form header values |
| **accentBg** | 19, 97, 134 | Left navigation bar background color, entity grid header background, numerous dialog header backgrounds |
| **accentFi** | 255, 255, 255 | Entity grid header font and icon color, numerous dialog header fonts and icons |
| **selectedBg** | 211, 237, 249 | Select row background on various controls (e.g file attachments, history rows), hovered row background on matching controls |
| **hyperlink** | 19, 98, 134 | Link values in a Form or other misc portal link items. |

Note that you can only have one theme configured for Portal at a time.

You can also replace the default Profisee logo with your organization's logo. To do so, navigate to the **PortalConfiguration**section of the swagger page and select the **portalconfiguration/icon** PUT request. You will be prompted to select a .png to replace the default image.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id5c7ce660a36ca90.png)