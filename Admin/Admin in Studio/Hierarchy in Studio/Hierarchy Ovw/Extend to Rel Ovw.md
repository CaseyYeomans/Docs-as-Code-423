# Extend to Relationship Overview

A Relationship is a complex structure, defining detailed characteristics of a foreign key that cannot be captured by the foreign key itself.

A DBA is a representation of a foreign key to the same or a separate entity. The DBA must be extended to be a Relationship before it can be used to build a hierarchy. The Relationship carries additional properties that define how it can be leveraged for operational purposes, including storage for metadata information provisioned when a Relationship is created.

A DBA, by itself, enforces data integrity of the specified attribute by ensuring the values of that attribute are constrained to the values specified in the associated foreign domain entity. Relationships allow modelers to specify additional semantic information about a data relationship that aid in understanding of the relationship and allow the system to enforce certain behaviors between the entities when changes are made to the associated entities. Relationships can convey aspects such as:

- Descriptions of the relationship in the form of relationship predicates. Two predicates exist for each relationship that describe the relationship from the perspective of each entity in the relationship. For example Customer **has** Contacts and Contacts **belong to a** Customer.
- Other aspects of the relationship might include aspects such as ownership, composition, containment, and mapping aspects.

A relationship can be extended either from the Hierarchy Designer or the tree view in Advanced Modeling. For detailed instructions on how to extend to Relationships in Profisee FastApps Studio, click the topic links below.

## See Also

[Extend DBA to Relationship in Advanced Modeling](https://support.profisee.com/wikis/profiseeplatform/extend_dba_to_relationship_in_advanced_modeling)

[Construct a Hierarchy Using the Hierarchy Designer](https://support.profisee.com/wikis/profiseeplatform/construct_a_hierarchy_using_the_hierarchy_designer)