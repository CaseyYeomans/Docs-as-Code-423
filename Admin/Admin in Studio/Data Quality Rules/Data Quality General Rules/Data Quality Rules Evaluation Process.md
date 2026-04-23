# Data Quality Rules Evaluation Process

The following master data activities trigger data quality rules:

- Real-time data changes (creates and updates) of members through the platform API
- On-demand requests using FastApps Studio or the Command Line Utility (CLU)
- Internal dependent member validation requests

## Rule First-Fail Process

A data quality rule consists of one or more clauses in a specific order. The platform rules engine operates on a first-fail basis, evaluating clauses associated with a rule in order of appearance in the rule designer panel. The evaluation process stops at the first assertion failure in the list. After a data steward fixes the first failure, the process continues until the attribute passes all clause assertions associated with the rule.

## Real-time Data Quality Rule Evaluation

Data quality rules run against entity members automatically when entity data is created and updated, including cases involving member data created or updated via the platform API:

- FastApps Studio and FastApps Portal data changes
- Matching and address verification strategy publishing processes
- Data deployment using FastApps Studio or Command Line Utility (CLU)
- Profisee Integrator external events
- Workflow data manipulation activities
- Custom integration performed using the SDK and web services generated using the Web Services Generator (WSG)

## Running Rules on Demand

Rule must be run explicitly when the following activities occur:

- Rules are added or changed by an administrator, rules are not run immediately and must be explicitly requested to run in order to re-evaluate the entity against the new or updated rules.

Run data quality rules explicitly via:

- FastApps Studio - Refer to [Run Rules on Demand using FastApps Studio](https://support.profisee.com/wikis/profiseeplatform/run_data_quality_rules_on_demand) for details.
- Command Line Utility - Refer to [Run Rules on Demand using the CLU](https://support.profisee.com/wikis/profiseeplatform/run_rules_on_demand_using_the_clu) for details.

## Dependent Member Validation

The platform rules engine automatically runs rules against an entity if data changes in a dependent entity. This is referred to as dependent member validation. Dependent member validation occurs when:

- A rule on one entity - entity A - references an attribute on another entity - entity B - through a domain-based attribute (DBA) relationship
- A rule on one entity - entity A - references a value on a different member in the same entity through a recursive DBA relationship

The dependency may be caused by a reference in a clause parameter or condition.

If data quality rules are not applied as expected, check the **Event Log** for error information.