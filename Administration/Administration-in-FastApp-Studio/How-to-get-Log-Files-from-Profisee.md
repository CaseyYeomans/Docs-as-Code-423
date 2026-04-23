# How to get Log Files from Profisee

# How to Get Log Files from Profisee

---

## Overview

This guide explains how to retrieve log files from your Profisee environment using the REST API. Log files are essential for troubleshooting issues and are often requested by Profisee Support when working on support cases. The process uses API authentication to securely access the LogEvents endpoint and download diagnostic logs.

## Prerequisites

Before you begin, ensure you have access to the following:

* **FastApp Studio**: Administrative access to Profisee FastApp Studio
* **API Key**: Ability to enable unattended authentication and generate an API key for your account
* **Profisee Environment URL**: The URL to your Profisee environment
* **Permissions**: Sufficient permissions to access the Accounts and Teams section and the REST API

## Step 1: Access Accounts and Teams

Navigate to the Accounts and Teams section in Profisee FastApp Studio:

1. Open Profisee FastApp Studio
2. In the left navigation panel, expand **Administration**
3. Click on **Accounts and Teams**
4. In the **Accounts** section, locate and select your user account

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic60be2c6f6e44ae6.png)

## Step 2: Enable Unattended Authentication and Copy API Key

Once you have selected your account, you need to enable API key authentication and copy the key:

1. Double-click your account to open the **Account Properties**.
2. Locate the **Unattended Authentication** section at the bottom of the pane.
3. Check the box to **Enable** unattended authentication.
4. Once enabled, a **Client ID** field will appear with your API key.
5. Click the **Copy** button next to the Client ID to copy your API key to the clipboard.
6. Click **Save and Close** to save your changes.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id56a2fc10f67cab3.jpeg)

Unattended authentication must be enabled for the API key to work. Keep your API key secure and do not share it with unauthorized users.

## Step 3: Navigate to the Profisee REST API Page

Access the Swagger/REST API documentation page for your Profisee environment:

1. Take your Profisee Portal URL (e.g., `https://yourcompany.profisee.com`)
2. Add `/REST` to the end of the URL (e.g., `https://yourcompany.profisee.com/REST`), then submit again.
3. The Profisee REST API swagger page page opens
4. On the Profisee REST API page, scroll down to find the **LogEvents** section. The LogEvents endpoint is a **GET** request: `/v1/logevents.`This endpoint retrieves event logs in reverse chronological order based on paging parameters
5. Click **Try it out** to expand it

## Step 4: Execute the API Call

Use the interactive API documentation to make the API call:

1. Locate the **x-api-key** field (API key for unattended authentication client ID).
2. **Paste your API key** (copied in Step 2) into the x-api-key field.
3. Click the **Execute** button. After a brief loading graphic, the **Responses** section appears with the API response.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3715ac5cefa7bd33.png)

## Step 5: Review the Response and Download Log File

After executing the API call, review the response and download the log file:

1. Check the **Server response Code**:
   * **200** = Success - the request was successful
   * Any other code indicates an error — double-check your API key and environment health.
2. If the response code is 200, you will see the **Response body** containing the log data in JSON format
3. Click the **Download** button to save the log file to your computer

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i8c980e32b760de76.png)

## Step 6: Attach Log File to Support Case

Once you have downloaded the log file:

1. Locate the downloaded log file on your computer (typically in your Downloads folder)
2. Navigate to your Profisee support case.
3. Attach the log file to your support case as a file attachment.
4. Add any relevant notes about when the issue occurred or what actions triggered it.

---

## Troubleshooting

### API Call Returns an Error (Non-200 Response Code)

If you receive a response code other than 200, try the following:

* **Verify API Key**: Ensure you copied the complete API key without any extra spaces or characters
* **Check Unattended Authentication**: Confirm that unattended authentication is enabled for your account
* **Verify Permissions**: Ensure your account has permissions to access the LogEvents endpoint
* **Check Environment Health**: Verify that your Profisee environment is running and accessible
* **Re-generate API Key**: Try disabling and re-enabling unattended authentication to generate a new API key

### Cannot Find LogEvents Endpoint

If you cannot locate the LogEvents endpoint:

* Ensure you are accessing the correct REST API page for your environment
* Check that your account has appropriate permissions to view API documentation
* Try refreshing the page or clearing your browser cache

### Download Button Not Appearing

If the Download button does not appear in the response:

* Verify that the response code is 200
* Check that the response body contains log data
* Try using a different web browser
* You can manually copy the response body and save it as a JSON file if needed

## Retrieving Additional Log Pages

The default page size is 50 log entries. To retrieve additional log entries:

1. Note the **TotalPages** value in the response
2. To get the next page, change the **PageNumber** parameter to 2, 3, etc.
3. To retrieve more entries per page, increase the **PageSize** parameter (maximum varies by configuration)
4. Execute the API call again with the new parameters
5. Download each page of results as needed

---

## Alternative Methods

While this guide uses the interactive REST API documentation, you can also retrieve logs using:

* **PowerShell**: Use Invoke-RestMethod with the API key in the headers
* **cURL**: Command-line HTTP requests with the x-api-key header
* **Postman**: API testing tool for making authenticated requests
* **Custom Applications**: Use the Profisee SDK or REST API in your own applications

### Example PowerShell Script

```
$apiKey = "your-api-key-here"
$baseUrl = "https://yourcompany.profisee.com"
$headers = @{
    "x-api-key" = $apiKey
}

$response = Invoke-RestMethod -Uri "$baseUrl/rest/v1/logevents?PageNumber=1&PageSize=50" -Headers $headers -Method Get
$response | ConvertTo-Json -Depth 10 | Out-File "profisee-logs.json"
```

---