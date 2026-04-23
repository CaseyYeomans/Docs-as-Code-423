# Enable App Registration Access

You must enable an App Registration (and its associated Entra Service Principal) to access your Warehouse. To do so:

1. Navigate to your Azure Portal and locate your App Registration. If you need to create an App Registration, see *Step 5* below.
2. Note the following information:
1. Application (Client) ID
2. Directory (Tenant) ID
3. Client Secret (create one if needed)
3. In the Microsoft Fabric portal, go to your workspace settings.
4. Under **Access**, add the App Registration/Service Principal:
1. Search for your App Registration by name.
2. Assign appropriate role (e.g., Contributor for read/write access)
5. Configure your application to use these credentials for authentication:
1. Use the Client ID, Tenant ID, and Client Secret.
2. Generate an access token using these credentials.
3. Include the token in your API requests to OneLake.

Remember to follow the principle of least privilege when assigning roles to your service principal.

## Finish

You have completed all the prerequisites for SQL Server and OneLake integration with Profisee Connect. You may now configure a [SQL Server](https://support.profisee.com/wikis/profiseeplatform/using_the_sql_server_service_provider) or [OneLake](https://support.profisee.com/wikis/profiseeplatform/using_the_onelake_service_provider) Service Provider in Profisee FastApp Studio.