# Integrating a non-SaaS Instance with Fabric

In order to connect Profisee's Fabric Workload to a Profisee IaaS (on-premise) or PaaS (cloud) instance, located behind a customer's perimeter firewall, customer network administrators should observe the following steps:

1. Create and update firewall rules to allow restricted traffic ingress from the following FQDNs for Profisee's Fabric workload:
- **frontend.fabric.profisee.com**
- **backend.fabric.profisee.com**
2. Create a public DNS record for the Profisee instance (ex. *profiseedev.customerdomain.com*) resolvable to the IP address(es) of your perimeter firewall(s).
3. Ensure the perimeter firewalls pass the Fabric HTTPS traffic to a reverse proxy, which should terminate the TLS tunnel and establish a new one to the PaaS/IaaS instance.
- If the Profisee PaaS/IaaS instance is using a **public CA leaf certificate**, the reverse proxy should be able to validate said certificate against the Public Issuing CA's Certificate Revocation List (CRL) endpoint.
- If the Profisee PaaS/IaaS instance is using an **internal CA leaf certificate**, the reverse proxy should be able to validate said certificate against the Internal Issuing CA's Certificate Revocation List (CRL) endpoint.

Note that PaaS deployments of Profisee that are not behind a firewall can connect Fabric to Profisee without additional configuration.