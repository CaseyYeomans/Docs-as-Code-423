# Build Advanced Connections for Importing Data

Import data from external database sources by building an advanced connection between the source file and Profisee.

The following procedure applies **only** to OLE DB for SQL Server.

1. From an Entity view, click **Import** on the entity grid toolbar.

The Import Data dialog appears. The Excel option is selected by default.
2. Select **Advanced**.
3. Click **Build**.

The Data Link Properties window opens. Connection to an OLE DB source is selected automatically from a list based on local settings and applications. To establish a different connection, click the Provider tab and then select the correct provider from the list.
4. On the Connection tab, configure the following settings:
- **Select or enter a server name**

Click the arrow to open a list of available servers. If the server you want to use is not displayed, click Refresh. If the server is still not displayed, contact your network administrator.
- **Enter information to log on to the server**

Select **Use Windows NT Integrated security** (recommended) to connect to the server with your current user account permissions.

**--or--**

Select **Use a specific user name and password** to log on as a different user, and then enter the account information and select **Allow saving password**.

You must select **Allow saving password** if you enter a specific user name and password. Otherwise, the connection will not be built and the connection string will be blank when you reopen the Data Link Properties dialog.
- Select the database on the server
- Click the arrow to open a list of available databases
- Select a database
5. Click **Test Connection**.

The Microsoft Data Link window opens and confirms that the test connection succeeded.
6. Click **OK**.
7. Click **OK** to save your settings and close the Data Link Properties dialog.

The Import Data dialog appears, and the **Table** field shows the name of the content table in the selected database.
8. Select the table or view from the Table list.
9. Click **Preview**.
10. Make sure the correct table is selected, and then click **Next**.
11. On the **Map selected columns to attributes** screen, use the top row of the table to establish a mapping between the source database column and a destination attribute in Profisee.

- Any source column without a matching destination attribute in Profisee is mapped to **<Ignore>** by default; any source column mapped to **<Ignore>** will not be imported.
12. Click the menu above each column header to view a list of available attributes to which you can map each source column.
13. If you are a system administrator, building the model as you import:

- To create a new attribute for any source column, select **Create New**.
- Select the attribute type (Free Form, Domain Based, or File) and associated attribute options in the Create Attribute dialog. For more information, see [Create Attributes](https://support.profisee.com/wikis/profiseeplatform/create_attributes).
- To create a new attribute defaulting to free-form text attributes for all unmapped source columns, click **Create new attributes**.
14. To discard your mappings, click **Back** to return to the previous window.
15. When your mappings are complete, click **Finish**.
16. Click **Yes** to acknowledge the confirmation window.

The new members are imported and appear at the bottom of the current grid view.

Selecting the **Preview records before publishing** option in the Import Data dialog defers publishing of imported records, in both live and deferred modes, until directed to do so by the user. This option is selected by default.

Select the **Automatically add domain values** option on the Import Data dialog to add new values from your imported data to source entities for DBAs. This option is selected by default. If it is not selected, new values will not be added.

In the Data Link Properties window, the Advanced tab displays advanced settings options according to the Provider you selected.

In the Data Link Properties window, the All tab displays a summary of your connection.

To save your mappings as part of your workspace, use the **Save** or **Save As** workspace options. The Import Data dialog then defaults to your custom mappings.