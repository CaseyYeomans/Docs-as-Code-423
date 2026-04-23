# Profisee REST API Overview

The Profisee API is an OpenAPI service that allows a user development access to entities, attributes, and members, as well as metadata and event data. The API accepts and returns JSON media types.

## Accessing the Profisee API

The Profisee API is installed automatically with the Profisee Platform, and no configuration is required to access it or the documentation. To access the API, open your web browser and enter your Profisee service URL followed by the endpoint **/rest**. This will direct you to the Profisee API documentation page.

![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i58ff0e31d01bf4e5.png)

## Using the REST API

A user can access and modify entity members and access metadata hosted in their instance of Profisee Platform in .JSON format. The Profisee REST API supports the OData specification. This includes metadata regarding paging, filtering, and sorting.

The Profisee REST API provides an OpenAPI standard documentation page built upon Swagger. The documentation page may be accessed using the endpoint **/rest/docs**. Each endpoint requires the user's Client ID (x-API-key) for authentication when initiating a call. Your ClientID can be found in **Accounts and Teams** in Profisee FastApp Studio. Click the endpoint to expand the documentation and try out the call by clicking the **Try It Out** button.

Note the following when working with data using the REST API:

- The ClientID used to make calls using the API must have sufficient permissions for the entity being accessed. Ensure this user obtains these permissions directly or from a team. Permissions gained from an Active Directory group are not sufficient.

- If you change the logging level within the .json file, the logging level is not automatically updated. You must reset IIS for this change to take place.

- If your entity name is a GUID (e.g. *6D0B2662-B989-439E-BD91-174F30AA942A*) or a number value (e.g. 123) you must use the internal ID or GUID in your REST requests instead of the name.

- When using endpoints that allow an array of requested items, take into account limitations in your local network for string length, payload length, and URI length.

### Odata Filter Operations

| | | |
| --- | --- | --- |
| **Operator/Function** | **Description** | **Example** |
| **OData Comparison Operators:** | | |
| eq | Equal | [city] eq 'Redmond' |
| ne | Not equal | [city] ne 'London' |
| gt | Greater than | [price] gt 20 |
| ge | Greater than or equal | [price] ge 10 |
| lt | Less than | [price] lt 20 |
| le | Less than or equal | [price] le 100 |
| **OData Logical Operators:** | | |
| and | Logical and | [price] le 200 and [price] gt 3.5 |
| or | Logical or | [price] le 3.5 or [price] gt 200 |
| not | Logical negation | not [price] le 3.5 |
| **OData Grouping Operators:** | | |
| ( ) | Precedence grouping | ([priority] eq 1 or [city] eq 'Redmond') and [price] gt 100 |
| **OData String Functions:** | | |
| concat | Concatenate specified values | concat(concat([City],','), [Country]) eq 'Berlin, Germany' |
| contains | |