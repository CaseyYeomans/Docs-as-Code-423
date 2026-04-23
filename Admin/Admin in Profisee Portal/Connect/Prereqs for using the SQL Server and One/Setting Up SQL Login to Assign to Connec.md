# Setting Up SQL Login to Assign to Connect to Browse the Server

Before you can use the SQL Server Service Provider, you must set up a SQL login for an on-premise SQL Server with the necessary permissions to connect, view, and manipulate data within the specified database. To do so:

## 1. Connect to SQL Server

1. Open SQL Server Management Studio (SSMS).
2. Connect to your on-premise SQL Server instance using an account with administrative privileges.

## 2. Set up the server for mixed (SQL Server & Windows Authentication) mode authentication

1. Right-click the server in the *Object Explorer* and select **Properties.**
2. Select **Security** in the **Select a page** list.
3. Under **Server Authentication** select **SQL Server and Windows Authentication mode.**

## 3. Create a SQL Login

1. In Object Explorer, expand the server instance.
2. Right-click the **Security** folder, then select **New**> **Login.**
3. In the *Login - New* dialog, enter a login name.
4. Select **SQL Server authentication** and set a password.
5. Uncheck **Enforce password policy** if not needed.
6. Click **OK** to create the login.

## 4. Grant Server-Level Permissions

1. In the Object Explorer, expand the **Security** folder, then **Logins**.
2. Right-click the newly created login and select **Properties**.
3. In the **Login Properties** dialog, go to the **Server Roles** page.
4. Check **public** to grant the login basic server-level permissions.
5. Click **OK**.

## 5. Grant Database-Level Permissions

1. Expand the **Databases** folder and select the database where you want to grant permissions.
2. Expand the database, then expand **Security** and right-click **Users**.
3. Select **New User**.
4. In the *Database User - New* dialog, set the **User name** to match the login name.
5. Set the **Login name** to the previously created login.
6. Click **OK** to create the database user.

## 6. Assign database Roles

1. In the Object Explorer, expand **Security** within the database.
2. Right-click the user and select **Properties**.
3. In the **Database User Properties** dialog, go to the **Membership** page.
4. Check the following roles:
1. **db\_datareader**: Allows the user to read data from tables and views.
2. **db\_datawriter**: Allows the user to insert, update, and delete data in tables.
3. **db\_ddladmin**: Allows the user to create, alter, and drop objects within the database.
5. Click **OK**.

## 7. Grant Additional Object-Level Permissions

Open a new query window and run the following commands, replacing <database\_name> and <login\_name> with your specific values:

```
USE <database_name>;
-- Grant connect and view permissions
GRANT CONNECT TO [<login_name>];
GRANT VIEW ANY DATABASE TO [<login_name>];

-- Grant permissions on all tables, views, and stored procedures
GRANT SELECT, INSERT, UPDATE, DELETE ON SCHEMA::dbo TO [<login_name>];
GRANT EXECUTE ON SCHEMA::dbo TO [<login_name>];
```

If specific permissions are required, you can grant them using T-SQL.

## 8. Verify Permissions

1. Log out from the current session and log in using the newly created login credentials.
2. Ensure the login can connect to the server, view databases, and perform the required operations.

## Finish

You have successfully set up a SQL Login with all necessary permissions. You may now continue to the next step, [Setting Up Authentication using OAuth 2.0 Resource Owner Password Credentials Flow](https://support.profisee.com/wikis/profiseeplatform/setting-up-authentication-using-oauth-20-resource-owner-password-credentials-flow).