# Staging FAQ

The following are answers to frequently asked questions about Staging administration:

- I received an error during staging. How can I tell what happened?

Error detail is logged in the **logging.tsystemlog** table. Examples of things that may cause an error are listed below. When an error occurs, the records that cause the error should remain in the staging table.

- DBA value does not exist.
- A unique constraint has been violated (constraint specified in Modeling).
- A Data Quality rule constraint has been violated.
- A Delete staging batch is trying to delete a member that is 'in use' (referenced by a different member)

- Why did both valid & invalid records remain in the staging table following an error?

If the members fail because of a SQL constraint (e.g. constraint specified in Modeling OR member in use) the error is returned by SQL and the entire batch is retained

- My error says the 'error limit is exceeded.' What does this mean?

The system setting **writing error limit** (default value = 1000) has been exceeded, and processing was stopped.

- What permissions are required to process staging?

In FastApp Studio, a user must have the **Batch Integration Admin** role with entity create and update permissions. If **Auto-Add DBA** is specified, that user must also have create permissions on the domain entities.

In SSIS or SQL, the user must have dbo\* or the Stg\_exec role. If the option **Enforce DQ constraint rules** is selected, the user must also be a Profisee user with permissions on the entity.

- Is there a way to run staging tables using a Managed Identity?

A workaround is required to use Managed Identities for running staging tables. When using a Managed Identity to handle authentication between services, you must add a user to Profisee with Super Admin privileges. The **Name** field of the user must be in the format [application\_id]@[tenant\_id]. Visually, it will appear as *GUID@GUID*.