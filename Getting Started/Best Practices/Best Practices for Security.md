# Best Practices for Security

Securing data is critical to maintaining trust, compliance, and operational integrity. This guide provides best practices for implementing robust security controls in Profisee MDM environments. It outlines strategies for authentication, authorization, encryption, and data protection, ensuring adherence to industry standards and regulatory requirements. Whether you manage on-premises or cloud deployments, this information will help you design a security plan to **minimize risk**, **enforce least privilege access**, and **support ongoing governance**.

MDM administrators and security professionals can use this guide as a reference to safeguard your data assets and maintain compliance across all environments.

### Identity and Access Management

Profisee uses a multi-layered approach to security.

- For authentication Profisee utilizes Single Sign-On (SSO) using OpenID Connect-compliant providers coupled with Multi-Factor Authentication.
- Authorization and data access are managed in the application using the security features.
- Profisee requires the use of a secure HTTPS connection, and a server certificate.
- For automation with Connect or the REST API you can provision user accounts with Client IDs.
- Data access for Reads and Updates can be restricted using row-level filters.

Whether using your own or Profisee Cloud infrastructure, customers are responsible for the management of their users, groups and roles via RBAC (Role-Based Access Controls).

Profisee software uses the principles of **Least Privilege Access**, requiring the minimum access necessary for productive work in each environment.

Profisee supports and recommends the use of security groups to efficiently maintain appropriate authentication and authorizations.

Profisee encrypts all communication using latest supported version of TLS. This includes **Client <-> API** and **API <-> API**.

### PAAS & Container Considerations

- Container base images are sourced from Microsoft, verified to be authentic, up to date and free of known vulnerabilities. The Kubernetes cluster is owned and managed by Microsoft. Profisee has no control over this in Azure (or Amazon's EKS). Please check with your cloud provider for their terms and service levels.
- Profisee provides regular updates to the container image to ensure the latest version of the web server application is used. We do not provide tools to scan images for vulnerabilities before deployment, but customers commonly do this with their own tools.

### Security Plan

This template lists the commonly deployed security settings for the key project roles. Customize the plan for your own teams, requirements and environments.

| | | | | | | | |
| --- | --- | --- | --- | --- | --- | --- | --- |
| **Security Roles** | **Key Project Roles** | | | | | | |
| **System Administrator** | **Solution Architect** | **Developer** | **Integration Developer** | **Subject Matter Expert** | **Enterprise Architect** | **Data Steward** |
| Address Verification Administrator | | Yes | | | Optional | | |
| Batch Integration Administrator | | Yes | | Yes | Optional | | |
| Data Archive Administrator | | Yes | | | | | |
| REST API Client ID | | | Yes | Yes | | | |
| Data Permissions | | Yes | Yes | Yes | | | Yes |
| Event Administrator | | Yes | | | Optional | | |
| Matching and Survivorship Administrator | | Yes | | | | | |
| Permission Administrator | | | | | Optional | | |
| Portal Administrator | | |