# Install Profisee FastApp Studio

Before installing the Profisee client, you must install the [.NET 8.0 hosting bundle and desktop runtime](https://dotnet.microsoft.com/en-us/download/dotnet/8.0) on any environment running Profisee FastApp Studio.

Install From the Application Server

To install the client from a Profisee server:

1. On the client, launch your web browser and open the following link to a Profisee Web application server in the cluster:

https://<ServerName>/<ProfiseeVirtualDirectory>/api/client/

For example:

https://corpltr4.corp.profisee.com/Profisee/api/client/

Use a Web services https connection to install the client. Do not include the port number.

For a SaaS instance:

https://profiseecloud.com/{yourinstancename}/api/client

2. Click **Install Profisee FastApp Studio**. The x64 version is recommended unless you are using a 32 bit version of Excel.
3. Download the selected version.
4. Click **Install**.

## Install From the Web Portal

To install the client from the Profisee support site:

1. Log in to [support.profisee.com](https://support.profisee.com/aspx/CustomerHome).
2. Click **Downloads** in the main toolbar.
3. Click **Profisee Platform** in the list.
4. Select the FastApp Studio folder for your version of Profisee.
5. Click **Download** under the 64-bit or 86-bit version of the .msi file, depending on your operating system. The x64 version is recommended unless you are using a 32 bit version of Excel.
6. Move the downloaded ZIP file to the computer where you want to install FastApps Studio.
7. Double-click the file to install it.

When installing the client using a FastApps Studio MSI file, you must manually configure the connection string the first time you connect. Refer to [Add A New Profisee Connection](https://support.profisee.com/wikis/profiseeplatform/add_a_new_profisee_connection) for details.