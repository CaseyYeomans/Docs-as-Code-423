# Using Connect with a Firewall

There are two methods to allow Connect to work with a firewall.

As an alternative to the instructions below: you can provide Profisee Support with your SQL server's Azure Resource ID, who will submit a private endpoint connection for your approval. Once approved, data will flow straight from Connect to the SQL instance in your Azure tenant.

## Customer-side with SQL Server 2022 as the Target (Recommended)

If this method is used, the same port can be re-used between Profisee environments as the user's reverse proxy will take care of processing and routing traffic based on the server name indication passed in the encryption request. For more information on Tabular Data Stream - click [here](https://learn.microsoft.com/en-us/sql/relational-databases/security/networking/tds-8?view=sql-server-ver17).

Ensure the following requirements are met:

1. Ensure that, whichever port is used in Connect, requests on the organization's end are restricted to Profisee's SaaS Egress IPs for both primary and secondary regions.
2. Configure your firewall to pass traffic coming from Profisee's egress IPs to a reverse proxy on the port chosen. To do so:
1. Set frontend listening to **1433**. You can also use ports **11000 through to 11999** in Connect. The 3 scenarios below best describe this process with an example port of 11111:
1. Port 1433: Connect sends traffic to customer's firewall port 1433, customer firewall passes 1433 traffic to customer's reverse proxy frontend on 1433 which passes it to reverse proxy backend SQL server port 1433.
2. Port 11111: Connect sends traffic to customer's firewall port 11111, customer firewall translates port 11111 to reverse proxy frontend listening on port 1433. Reverse proxy backend passes it to SQL server port 1433.
3. Port 11111: Connect sends traffic to customer's firewall port 11111, customer firewall passes 11111 to reverse proxy frontend listening on port 11111. Reverse proxy backend translates it to SQL server port 1433.
2. Set the frontend **bind** option to: alpn tds/8.0 as Tabular Data Stream will be the sole protocol (*Optional but recommended).*
3. Set the frontend mode to: mode tcp.
4. Create a backend with the required SQL server added to it, also set to: mode tcp.
5. Set two ACLs on the frontend:
1. Check for TLS1.2 Client Hello: req.ssl\_hello\_type 1
2. SNI match for the backend SQL server: req.ssl\_sni -i SomeServerName.Domain.com
6. Complete the following actions on the front end in this order:
1. Request delay for tcp inspection: tcp-request inspect-delay 5s (can work with 2s, even 1s).
2. Accept only if TLS Client Hello is detected: tcp-request content accept if req.ssl\_hello\_type 1
3. Match the SNI and send to SQL backend: use\_backend <name of backend> if req.ssl\_sni -i SomeServerName.Domain.com
3. Install a **public** certificate on the on-prem SQL server 2022. More info [here](https://learn.microsoft.com/en-us/sql/database-engine/configure-windows/manage-certificates?view=sql-server-ver16).
4. Configure your service configuration in Connect as below. Leave **Trust Server Certificate** unchecked.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id9adebf8d5a85468.png)

## Customer-side with SQL Server 2019 as the Target

This requires port forwarding, as TDS v7.x does not support **Encrypt=Strict**, only **Encrypt=true/false**,**Encrypt=on/off**, and **Encrypt=optional/mandatory**. Due to how TDS 7.x protocol operates, once a TCP connection is established, the client will send a clear text TDS message that will not be understood by a reverse proxy, and the SNI inside the TDS request will not be matched, resulting in the request being dropped.

1. Whatever port is used in Connect, requests on the organization's end must be restricted to Profisee's SaaS Egress IPs for both primary and secondary regions.
2. Use dedicated ports in each Profisee environment. For example:
1. Customer Profisee Dev instance connecting to a Dev SQL 2019 target on-prem server uses 11000
2. Customer Profisee Test instance connecting to a Test SQL 2019 target on-prem server uses 11001
3. Customer Profisee Prod instance connecting to a Prod SQL 2019 target on-prem server uses 11002
3. Configure your firewall to accept and NAT traffic coming from Profisee SaaS egress IPs to respective backend SQL servers. Example:
1. Port 11000, Connect sends traffic to the user's firewall port 11000, which is translated to 1433 and passed to Dev SQL server 2019
2. Port 11001, Connect sends traffic to the user's firewall port 11001, which is translated to 1433 and passed to Test SQL server 2019
3. Port 11002, Connect sends traffic to the user's firewall port 11002, which is translated to 1433 and passed to Prod SQL server 2019.
4. If using Perimeter and Internal firewalls, traffic should be processed to reach the SQL server on whichever port it is expecting traffic.

Do not set **Encrypt Communications** to **Optional**, as this will result in unencrypted TDS v7.x traffic between Profisee and target SQL server.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3ba19dc3c1831a6e.png)
If **Encrypt Communications** is set to **Mandatory**, this will result in encrypted TDS v7.x traffic between Profisee and target SQL server. A public certificate needs to be installed on the target SQL server.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5ddb76bba5acec47.png)
If this option is chosen and the certificate on the target SQL server is NOT public (or has expired), then the **Trust Server Certificate** option must be checked.