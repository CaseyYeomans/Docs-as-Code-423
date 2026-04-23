# Best Practices for Staffing

Successful **Master Data Management** (MDM) projects depend on having the right people in the right roles at the right time. This guide provides practical recommendations for staffing Profisee MDM projects, ensuring alignment with business objectives and technical requirements. Whether you are planning a small analytical solution or a complex enterprise integration, this guidance will help you build a team that can deliver quality outcomes efficiently. Included are role definitions, pre-requisite skills, best practices, and a RACI matrix to clarify responsibilities throughout the project lifecycle.

Use this guide as a reference to set your project teams up for success and optimize resource allocation, and as a blueprint for building and sustaining high-performing teams.

### Key Principles for Success

- **Business & Technical Sponsorship**: Secure executive and technical champions for alignment and support
- **Right Roles, Right Time**: Assign resources based on project complexity and phase
- **Incremental Success**: Deliver value iteratively; avoid over-engineering early stages
- **Leverage Expertise**: Use out-of-the-box features and incorporate vendor/partner experience
- **Governance Matters**: Establish a governance council and data stewardship for quality assurance

### General Best Practices

Alongside Profisee-specific recommendations, it's essential to apply established IT best practices to ensure overall project success.

- MDM programs and projects are more likely to succeed if they have a business sponsor as well as technical sponsors.
- Understand the project's business goals and leverage your subject-matter experts (SMEs).
- Use project managers to identify and manage risk.
- Follow your standard IT and project best practices.
- Don't let perfection get in the way of good enough. Incremental success is valuable.
- Leverage out-of-the-box behavior and functionality before creating custom solutions.
- Establishing an MDM center of excellence delivers long-term benefits like repeatable success, faster deliveries, and reduced team turnover.
- Incorporate software vendors and partners into your internal team to benefit from their combined experience.
- Note that some organizations may need governance and program management resources in addition to MDM roles.

### Team Composition and Project Duration

| | | | |
| --- | --- | --- | --- |
| **Project Size** | **Characteristics** | **Team** | **Duration (Median)** |
| Small | One data domain Analytical use case | 1-2 FTEs Project Manager Solution Architect SME | 4-6 weeks |
| Medium | Multiple domains Operational integrations Contribute/Approve workflows | 3-4 FTEs Project Manager Integration Developer Solution Architect SME | 12 weeks |
| Large | Multiple domains Multiple systems integrations Complex workflows High data volume Real-time & batch processing | 5-8 FTEs Project Manager Solution Architect(s) SME Developer(s) Integration Developer(s) | 6 months |

Ongoing operations and maintenance requires a small ad-hoc team for enhancements and support. System administration resources are required for all projects. Effort levels vary by deployment type.

| | |
| --- | --- |
| **Deployment Type** | **Effort** |
| SaaS | Minutes |
| IaaS/On-premise | Hours |
| PaaS | Days |
| Private PaaS | Weeks |

### Project Roles

The following table outlines the roles and responsibilities of those on a Profisee MDM team. Project roles are different than the security roles provided by Profisee. See the [Best Practices Guide on Security](.) to learn how project and security roles work together.

| | | | |
| --- | --- | --- | --- |
| **Role** | **Responsibilities** | **During Project** | **After Go Live** |
| Sponsor | The project sponsor ensures strategic alignment, secures resources, provides executive oversight, manages escalated risks, champions the project, and approves key decisions and deliverables. | Up to 10% | Ad-hoc |
| Project Manager | Develops and manages project plans, ensures timely quality deliverables, and reports project progress. Responsible for management and escalation of risks, assumptions, issues and dependencies (RAID). | Up to 100% | None |
| System Administrator | Technical resource with administrative privileges on networks, servers, and databases. Assists with installation, configuration, and upgrades of servers and software. | 1-2 days per environment | Occasional support |
| Solution Architect | Configures and administers Profisee solutions. Typically includes modeling, strategy design, user interface and data quality configuration, and some integration. Often is a data management professional with experience in developing MDM, data warehousing, business intelligence, or database applications. | Up to 100% | Occasional support |
| Developer | Implements data and system integrations, workflows, and extends the Profisee platform with webhook applications and the Profisee REST API. | Up to 100% | Occasional support |
| Integration Developer | Responsible for loading source data from and publishing results to analytical and operational systems. Uses Connect and ETL tools to interact with Profisee's REST API. | 1-2 weeks per domain / system | Occasional support |
| Subject Matter Expert | Resources who are familiar with the data and business processes related to the MDM solution. Provides deep knowledge of application functionality and requirements. Participates in design workshops, as well as planning and execution of testing. | Up to 50% | Occasional support |
| Enterprise Architect/Data Modeler | Oversees the conceptual, logical, and physical data models that conform to an organization's standards and conventions. Provides leadership and guidance with enterprise data strategies, especially as they relate to MDM and governance. | Up to 10% | Occasional support |
| Data Steward | Individuals who interact with data and processes as part of their day-to-day work. These are the business users of the MDM system. | Up to 10% | Up to 100% |
| Governance Council | The decision and policy-making authority for data. They oversee the implementation of standards and quality assurance to ensure the MDM team and Data Stewards are developing, maintaining, and providing acceptable system data for the use of others. | Ad-hoc | Ad-hoc |

- MDM teams commonly have individuals who perform several roles.
- Analytical solutions can be implemented in Profisee by very small teams (or an individual) assuming they have the requisite system, data, and tools access.
- Larger scoped projects, like those that integrate with operational systems, typically require 3-8 resources.
- MDM project teams can be augmented with certified consultants from Profisee's Professional Services team or a Systems Integrator.
- Changes to the business requirements and technical landscape are predictable, so we recommend MDM programs maintain a small internal team for ongoing operations and enhancements.

### Prerequisites

Before learning about the Profisee platform, it is highly recommended that individuals in the following roles be familiar with the following topics.

| | |
| --- | --- |
| **Role** | **Pre-Requisite Knowledge** |
| System Administrator | PaaS - Kubernetes (Azure or AWS or GCP); IaaS - Windows & IIS |
| Solution Architect | Familiarity with SQL (Azure or Enterprise) |
| Data modeling concepts like tables and columns, relationships and foreign keys |
| Developer | Visual Studio and C# (required for Workflow development and testing) |
| Azure Data Factory or a similar ETL tool |
| Webhook application development (Azure Functions/Logic Apps/etc.) |
| Familiarity with REST APIs and tools like Postman & Swagger pages |

### RACI Matrix

This template lists the common activities and deliverables in an MDM project. You should customize this matrix for your projects as needed.

- **R** = **Responsible**. Executes the task.
- **A** = **Accountable**. Owns outcome and makes decisions.
- **C** = **Consulted**. Provides input and expertise.
- **I** = **Informed**. Must be kept updated on progress.

| | | | | | | | | | | |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **Activity** | **Project Sponsor** | **Project Manager** | **System Admin** | **Solution Architect** | **Developer** | **Integration Developer** | **SME** | **Enterprise Architect** | **Data Steward** | **Governance Council** |
| Project Plan | A | R | I | C | I | I < |