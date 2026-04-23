# Best Practices for Upgrades

Software upgrades are a critical component of maintaining a secure, efficient, and competitive technology environment. As businesses increasingly rely on software to drive operations, manage data, and deliver services, ensuring that these systems remain current is essential. Upgrades provide more than just new features--they address security vulnerabilities, improve performance, enhance compatibility, and support compliance with industry standards.

Companies perform software upgrades to reduce risk, optimize productivity, and leverage technological advancements. Using outdated software can expose organizations to support problems, cybersecurity threats, operational inefficiencies, and integration challenges. By adopting a structured approach to upgrades, businesses can minimize downtime, control costs, and ensure a smooth transition for users.

This document outlines best practices for planning, executing, and validating software upgrades. Following these guidelines will help organizations maintain system integrity, protect sensitive information, and maximize the value of their technology investments. The objective is to have the right version of the software installed securely, with the least effort and cost possible.

This document, in conjunction with Profisee's [Release Notes](https://support.profisee.com/wikis/release_notes/) and [Help](https://support.profisee.com/wikis/profiseeplatform/), will enable you to select the appropriate version for your organization and plan your upgrade project.

### Infrastructure

- **Software as a Service (SAAS)**
- Profisee hosts and manages the Customer's software.
- Initial setup is rapid and requires 1 hour of your System Administrator's time.
- Upgrades are achieved in minutes via a Technical Support case.
- **Infrastructure as a Service (IAAS)**
- Customer installs and deploys the software on a Windows Virtual Machine (VM).
- If you don't have hardware capacity to deploy then purchasing can require a long lead time and in extreme cases this can delay projects by weeks.
- When you have the VM ready for use the initial setup by the System Administrator usually takes less than 1 day.
- Upgrades can be achieved in less than 1 day.
- **Platform as a Service (PAAS)**
- Customer installs and deploys the software on their cloud using Kubernetes.
- The time and effort required for installation and upgrades can vary greatly.
- Installs and upgrades can be performed in minutes if you use the Azure Resource Manager (ARM) Template provided. Although this template may not align with your IT standards and policies, we recommend it as a starting point for PAAS installation.
- Most customers can install and upgrade the software in a few hours.
- Implementing a private PAAS environment can be highly complex, sometimes requiring your System Administrator to spend several days working over multiple weeks.
- Changing infrastructure when doing an upgrade introduces a little more complexity. For example, when Customers switch from IAAS or PAAS to SAAS, the old system must be upgraded to the minimum supported version before the solution migration is performed.

### Upgrade Projects

- **Research**

- Select the version to upgrade to based on your solution's feature usage and our release notes. When selecting a version to upgrade to, see if there has been a big architectural change in the features you are using most, to determine the level of testing and disruption to your current configuration. For example there was a big change in DQ rules in 24R1, and a big change in Matching in 25R2, so consider that when upgrading. A few minutes reading the upgrade considerations documentation will answer most of your questions.
- Aisey can help you select the best version and create a checklist for your scenario.
- **Installation**

- The install guides in the documentation detail the specific tasks for each scenario.
- **Testing**

- Always perform a smoke test post-upgrade.
- System, performance, and user acceptance testing can require days, weeks, or months of effort, depending on your specific use case and scenario. Examples below.
- Testing an upgrade on a system not yet in use in production requires less effort.
- Testing an upgrade with multiple operational system integrations can be complex and require formal test plans for your solution based on your specific business requirements.
- Upgrade projects can sometimes require dedicated performance testing when using processing intensive features like Matching and Connect with very large data volumes (tens or hundreds of millions of records).
- **Communication**

- Record changes in system logs.
- Communicate the change to your users.

### Downgrades

- Do not downgrade. In the unlikely event of an error or a failed upgrade, or if you experience other issues with the upgraded instance, it is recommended to contact Profisee support for assistance to resolve any issues.
- If you want to revert to an earlier version, you can restore the database and file repositories from the backups you made prior to the upgrade.
- Profisee does not support downgrading its software versions. The database upgrade is not reversible - the platform is designed for upgrades, and there are no documented procedures or tools for reverting to an earlier version. Downgrading would likely result in compatibility issues, data integrity problems, and unsupported configurations.

### Support and Compatibility

- Profisee software leverages many of Microsoft's software products.

- Profisee uses only Microsoft's current Long-Term Support (LTS) releases, avoiding short-term supported versions.
- For example, with .NET we went from v6 to v8, and are planning to upgrade to v10 before v8 support expires in late 2026.
- We are working to make Profisee possible to deploy on Linux. No timeline for this can be shared currently.
- Depending on your current version, and the version you select for your upgrade, you may need to perform multiple upgrades or adjust your solution to handle deprecated features. Review the [upgrade considerations](https://support.profisee.com/wikis/release_notes/cumulative_upgrade_considerations) documentation for details.
- Profisee supports all versions of our software, but generally only provides fixes for current year versions.
- If database customizations are present before the upgrade, ensure they are removed prior to the upgrade attempt.

### Upgrade Checklist

1. Identify your scenario:

- What is your infrastructure approach?
- Are you doing an upgrade-in-place, or a parallel install which you will deploy solution artifacts to?
2. Review the system and server pre-requisites in the documentation. This includes the version specific AND general upgrade considerations.
3. Download the relevant files.
4. Optionally, you can use the current version of the CLU or the Portal administration pages to export solution artifacts to the file system - refer to the Help or the [Best Practices Guide for Deployment](https://support.profisee.com/wikis/profiseeplatform/best_practices_for_solution_deployment).
5. MANDATORY - backup the database and the file repository immediately before installing the new version of the software.
6. MANDATORY - install the required software for your scenario:

- Platform - only required for IAAS
- Studio
7. Optionally, for data integration we recommend using Connect and the REST API instead of CLU and Integrator. Workflow currently still relies on the SDK, but a new solution will be provided in future releases. Upgrading and continuing to use these three legacy features is not recommended. They will not be supported long term.
8. Follow the installation instructions in the help for your scenario.