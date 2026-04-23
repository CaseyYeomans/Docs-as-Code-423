# Profisee Maintenance Guide

All systems need maintenance to remain effective and efficient. This document is a guide to the maintenance processes for all versions and deployment approaches of the Profisee platform. Refer to the online documentation at [https://support.profisee.com](https://support.profisee.com/) or the relevant vendor's website for how the referenced features work.

### Disclaimers

- This document was created when 2023R1 was generally available, and guidance may change in the future.
- Changes or updates to all systems should be tested in a non-production environment before being applied to your production environment.
- If we have missed something, please let us know.

### Infrastructure Maintenance

| | | | |
| --- | --- | --- | --- |
| **Task** | **IaaS** | **PaaS** | **SaaS** |
| Windows updates | Yes | No | Profisee |
| NGINX | No | Yes |
| [Upgrade Kubernetes](https://support.profisee.com/wikis/profiseeplatform/maintenance_best_practices) | No | Semi-annually |
| [Restart pods for updates](https://support.profisee.com/wikis/profiseeplatform/maintenance_best_practices) | No | Monthly |
| [Backup settings.yaml file](https://support.profisee.com/wikis/profiseeplatform/maintenance_best_practices) | No | Use Azure Key Vault |
| [Regenerate secrets](https://support.profisee.com/wikis/profiseeplatform/maintenance_best_practices) | No | Optional |
| Remove redundant environments | Yes | Yes |
| Server scaling | Manual | Configurable |
| Remove redundant client software | Yes | Yes | Yes |

### Database Maintenance

Maintenance tasks vary depending on your choice of database implementation.

| | | | | |
| --- | --- | --- | --- | --- |
| **Task** | **SQL Server** | **Azure SQL** | **AWS RDS** | **ProfiseeCloud** |
| SQL - Service packs & updates | Monthly | No | ? | Profisee |
| SQL - Database backups | Daily | No | ? |
| SQL - Check database integrity | Weekly | No | ? |
| SQL - Reorganize indexes | Weekly | No | ? |
| SQL - Update statistics | Weekly | No | ? |
| SQL - Cleanup history | Weekly | No | ? |
| SQL - Maintenance cleanup | Weekly | No | ? |
| Select a maintenance window | Yes | default | ? |
| Prof - History maintenance script | V7-v2022R2 v2022R1 only | | | N/A |

### Profisee Application Maintenance

| | |
| --- | --- |
| **Task** | **Suggested Schedule** |
| Remove inactive user accounts | Quarterly |
| Remove redundant entities and attributes | Quarterly |
| Profisee license maintenance | Annually |
| Set the History retention limit | Annually |
| Set the Event message retention | Annually |