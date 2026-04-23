# Using the Melissa Data Personator Service Provider

The **Melissa Data Personator** service provider is available by default within all instances of Profisee 2024.R1 and beyond. Unlike custom service providers, Melissa Data Personator can be selected from the [Service Provider](https://support.profisee.com/wikis/profiseeplatform/service_providers) list as soon as your instance is upgraded to 2024.R1 or later. For additional information about using the Melissa Data Personator Consumer API, click [here](https://devconsole.melissadata.com/personator/).

As of 2024.R1, the only available service for this provider is the **Verify Contact** service, which includes two operations:

- **Realtime Contact Verify**: This option sends a HTTP GET request. The get operation is used to perform real time (single record) requests for contact verification.
- **Batch Contact Verify**: This option sends a HTTP Post request. The post operation is used to perform batch-based requests where Personator can verify up to 100 records per request.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3124659c8008ff8b.png)

Once the service provider is configured, the Settings tab for this service provider includes the following options:

- **License Key:** This option raises a Credential dialog, allowing the user to provide their API key to Personator. This is a required field.
- **Actions:**This option determines which action the service will perform on the input data. While all actions are presented, the user should only select the actions that are allowed with their license. This is a required field.
- **Columns to Return:**This option specifies which columns are returned. Personator Consumer allows the user to select what data the service will output. The Columns input field allows the user to select either individual columns or groups, which are returned in the output. These selected columns are returned in addition to the default columns, which are always returned. More information, including column definitions, can be found [here](http://wiki.melissadata.com/index.php?title=Personator:Output_Columns).

You must select the columns you wish to map in your strategy.

- **Request Options**: the Options section allows you to configure a number of options that change the way the service behaves. See Personator docs for more information on the available settings.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id2645b754cfd62df.png)