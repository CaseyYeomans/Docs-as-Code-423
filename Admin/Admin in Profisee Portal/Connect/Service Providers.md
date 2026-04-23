# Service Providers

When managing connections, a **Service** is the external platform to which Profisee connects. **Service Providers** define the services and resources provided to Profisee when connected. Profisee users can either use pre-configured service providers that are ready to use out of the box, or create their own **RESTful Service Provider**: a service provider that is accessed via a REST endpoint which provides services statically through an OpenAPI specification.

One *Melissa Data Personator* service provider is included in the Profisee Platform by default, and more default service providers will be included in future releases. Default service providers cannot be edited or reconfigured. Additional service providers can be created and configured using a generic REST API gateway. More information on creating a service provider can be found on the [Profisee GitHub](https://github.com/Profisee/connectors).

Service Providers allow you to conduct external operations within Profisee. For example, the above *Melissa Data Personator*service provider allows users to use Melissa Data's Address Verification services within their instance of Profisee. By creating your own service providers, you can add functionality to your Profisee instance to meet needs unique to your organization.

From the **Service Providers**tab on the Portal Administration page, you can view and edit any configured service providers. You cannot edit or delete a service provider that is currently in use. The Service Providers Tab includes the following information:

- **Name**: The name of the service provider. Clicking the name allows you to edit the Service Provider.
- **Type**: The type of service, including Rest, Database, File, Script, or AI.
- **Source**: The platform the service provider is connected to.
- **Updated On**: The date and time the Service Provider was last updated.
- **Updated By**: The user that last updated the Service Provider.

### Import or Export a Service Provider

You can import a new service provider to Profisee Connect by clicking the vertical ellipsisicon in the Service Provider toolbar, then click **Import**. Select a .JSON file from your device that accurately maps out the service provider connection, then click Open. The new service provider is added to the list.

To export a service provider to a .JSON file on your device, right-click a service provider from the list or select the ellipsis icon beside it, then click Export (Selected).

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i165fafa467dd1b3f.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i238d15c0f91566c8.png)