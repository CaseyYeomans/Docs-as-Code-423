# View Data Quality Rules

Rules administrators can view system rules from the Data Quality Rules administration tab. A grid displays the following information:

| Column | Description |
| --- | --- |
| | The flag column displays error and warning indicators when there are configuration issues detected on rules. |
| Entity | The entity to which the rule is associated. |
| Attribute | The attribute of the entity to which the rule is associated. |
| Updated On | The date and time the rule was last updated. |
| Updated By | The domain name of the user that last updated the rule. |
| Created On | The date and time the rule was created. |
| Created By | The domain name of the user that created the rule. |
| Validation | Shows if the rule contains validation rule clauses. |
| Constraints | Shows if constraints are enabled for a validation rule. Constraints prevent the record from being created or updated if the validation rule is violated. |
| Assignments | Shows if the rule contains assignment clauses to populate attribute values. |
| Assignment Execution Mode | Denotes when the assignment rule will be applied: (always, on create only, on update and on demand) |

By default, the rules grid is sorted by entity and attribute in ascending order. You can sort the rules by any column heading listed above except for the flag, validation, constraints, or assignment columns. Click the column header to sort ascending or descending.

To filter rules for a specific entity, select the entity from the dropdown list in the administration toolbar. Select the blank selection at the top of the dropdown to clear the filter.