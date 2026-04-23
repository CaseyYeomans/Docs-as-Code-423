# Impact of Modeling and Rule Changes on the Data Quality Data Mart

Administrative changes to the master data model and data quality rules impact collected information about data quality in the **Data Quality Data Mart**.

## Effects on Data Quality Issue Facts when the Rule Changes

The Data Quality Data Mart features a FactDataQualityIssue view to detect and track the status of data quality issues. The table below describes the effects on the Data Quality Issue Fact view of various rule administration activities.

| Rule Administration Activity | Effect on FactDataQualityIssue |
| --- | --- |
| A clause is inserted above other clauses in the rule. | If the ordinal position of a clause is changed, any facts associated with it are closed and marked as obsoleted. |
| A clause is deleted. | Any open facts associated with the deleted clause are closed and flagged as obsoleted. If the ordinal position of a clause is changed due to the deletion, any facts associated with that clause are closed and marked as obsoleted. |
| A clause is changed by changing its assertion type, parameter, or condition. | Any facts associated with the updated clause are closed and flagged as obsoleted. |
| A rule is added to an attribute. | This has no immediate effect on the fact table. However, when rules are run automatically or on demand, new facts may be opened in the fact table based on the new rule and its clauses. Refer to [Data Quality Rules Evaluation Process](https://support.profisee.com/wikis/profiseeplatform/data_quality_rules_evaluation_process) for further details. |
| A rule is deleted from an attribute. | All open facts that are associated with all of the facts clauses are closed and flagged as obsoleted. |
| A clause is added to the rule at the end. | This has no effect on existing facts in the fact table. |

## Effects on Data Quality Issue Facts when the Model Changes

Changes in the underlying master data model the data quality rules define may also impact data quality issue facts collected in the Data Quality Data Mart. The table below describes the effects that various modeling activities have on information collected in the data mart.

| Modeling Activity | Effect on FactDataQualityIssue |
| --- | --- |
| Deleting an entity | All facts related to rules and clauses associated with the entity are deleted from the underlying fact table, and the associated validation issues table. |
| Deleting an attribute | All facts related to the rule and clauses associated with that attribute are deleted from the fact table, and the entity's underlying validation issues table. |
| Renaming an entity | This has no effect on existing facts, as the association between the data quality facts and the entity is by global ID and not name. |
| Renaming an attribute | This has no effect on existing facts as the association between the data quality facts and the attribute is by global ID and not name. |