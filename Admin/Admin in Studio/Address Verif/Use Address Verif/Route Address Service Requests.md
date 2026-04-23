# Route Address Service Requests

To configure how address service requests are routed:

1. Click **Settings** in the Profisee Desktop toolbar.
2. Navigate to **System Settings | Address Verification**.
3. Complete the proxy server settings:

- In the **HTTP proxy URL** field, enter the URL of the proxy server handling HTTP requests on your network.
- In the **HTTPS proxy URL** field, enter the URL of the proxy server handling HTTPS requests on your network.

Enter the proxy server URL in the following format:

http[s]://proxyServerName:portNumber

If your network has one proxy server handling both HTTPS and HTTP requests, enter the same URL in both fields. If no proxy information appears in the settings fields, then no proxy is used. Currently, **Bing** and **Loqate** use HTTP requests. **Melissa Data** and **Google** use HTTPS.

Profisee does not support Proxy auto-configuration scripts.