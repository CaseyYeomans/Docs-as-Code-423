# Viewing Purview Governance Information in FastApp Portal

Users can view governance information collected and enriched by Azure Purview through Profisee FastApp portal to view detailed information about a Profisee instance, entity, or attribute. Profisee Instance governance details can be found in the **Governance Instance tab** within the Help dropdown menu, while Entity and Attribute governance details can be accessed from the Governance Details icon on an Entity Grid header or above attribute fields in Forms.

This governance information is collected from the metadata of the instance, entity, or attribute as it is configured in Profisee FastApp studio, then further refined by users with privileges to edit Governance information in Azure Purview. This allows users to view detailed information about their data, including classifications, properties, and contact information relevant to the asset in Profisee FastApp Portal.

## Viewing Governance Details

When inspecting the governance information for an instance, entity, or attribute in the portal, users can view information within five different tabs: Overview, Classification, Glossary, Experts, and Owners.

## Overview

The Overview tab displays the enriched metadata created for this instance, entity, or attribute. Unlike the other tabs, the information displayed on this tab differs depending on whether the asset is an Instance, Entity, or Attribute. This tab displays the following pieces of information for each data type.

#### Instance

- **Description**: User-defined description for the instance defined in Purview
- **External URL**: URL link to the Profisee portal instance
- **Gateway URL**: URL link to access the Profisee REST gateway

- **Profisee Platform Version**: The version of the Profisee Platform running on this instance.
- **Created On**: The date the instance was created.
- **Updated On**: The date the instance was most recently updated.

#### Entity

- **Description**: User-defined description for the entity.

- **Code Generation Enabled**: Defines whether the Code value is automatically generated for this entity.
- **Code Generation Seed**: The starting value for the generation of the Code value.
- **History Mode**: The [logging level](https://support.profisee.com/wikis/profiseeplatform/log_audit_information) for the entity.
- **History Retention Days**: The number of days that changes to this data are recorded before being removed.
- **Has File Attached**: Whether the entity is configured for File Attachments.

- **Icon Name**: The name of the display icon for this entity.
- **Created On**: Datetime when the entity was created.
- **Created By**: User that created the entity.
- **Updated On**: Datetime when the entity was most recently updated.
- **Updated By**: User that updated the entity.

#### Attribute

- **Attribute Type**: The data type of this attribute, such as Text, Numeric, Domain List, or DateTime.
- **Maximum Text Length**: For Text and Link attributes, the maximum number of characters available for the attribute.
- **Decimal Precision**: The number of decimal spaces for Numeric attributes.
- **Domain**: The entity used as the domain for a Domain Based Attribute (DBA).

- **Domain Entity is System-aware**: Whether the domain entity has an attribute that is a system-aware attribute.
- **System-aware Attribute**: Whether this attribute is used to store the unique identifier from an external system.
- **External System Name**: The name of the external system if this attribute is a System-aware attribute.
- **Is Restricted**: Whether this attribute can be updated.
- **Must Be Unique**: Whether there can be more than one record with the same attribute value.

- **Default Value**: The value this attribute is set to automatically (if any).
- **Created On**: Datetime when the attribute was created.
- **Created By**: User that created the attribute.
- **Updated On**: Datetime when the attribute was most recently updated.
- **Updated By**: User that most recently updated the attribute.

### Classifications

The Classification tab provides data stewards access to categorizations defined in Purview. This information includes the Display Name, Formal Name, and Description for the asset.

### Experts and Owners

The Experts and Owners tabs display contact information for users and teams who are relevant to this asset. This may include names, email addresses, and phone numbers, as well as optional additional points of contact such as Microsoft Teams or Slack.

### Glossary

The Glossary tab provides the data steward with detailed information and definitions for the data they are viewing. This includes a description of important terminology relevant to the subject, acronyms associated with the subject, and links to related resources for information that is beyond the scope of the description.