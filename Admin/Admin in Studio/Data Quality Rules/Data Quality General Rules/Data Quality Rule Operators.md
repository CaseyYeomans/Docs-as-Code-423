# Data Quality Rule Operators

The table below lists operator types supported by the data quality validation rules engine. The datatype of your attribute will determine which validation rule operators are available.

## Validation Rule Operators

| Assertion | Parameters Required | Condition Required | Associated Attribute is Invalid When ... |
| --- | --- | --- | --- |
| is valid | none | yes | The required condition is false. |
| is not valid | none | yes | The required condition is true. |
| is required | none | no | The attribute is blank (null) and a condition is not specified, or a condition is specified AND is true. |
| must be blank | none | no | The attribute is non-blank (non-null) and the optional condition is unspecified OR true. |
| must not equal | 1 | no | The attribute does not equal the specified constant or attribute parameter AND the optional condition is unspecified OR true. |
| must equal | 1 | no | The attribute equals the specified constant or attribute parameter AND the optional condition is unspecified OR true. |
| must be less than | 1 | no | The attribute is greater than or equal to the specified constant or attribute parameter AND the optional condition is unspecified OR true. |
| must be less than or equal to | 1 | no | The attribute is greater than the specified constant or attribute parameter AND the optional condition is unspecified OR true. |
| must be greater than | 1 | no | The attribute is less than or equal to the specified constant or attribute parameter AND the optional condition is unspecified OR true. |
| must be greater than or equal to | 1 | no | The attribute is less than the specified constant or attribute parameter AND the optional condition is unspecified OR true. |
| must contain | 1 | yes | The attribute does not contain the specified constant or attribute parameter AND the optional condition is unspecified OR **true**. |
| must not contain | 1 | yes | The attribute does not contain the specified constant or attribute parameter AND the optional condition is unspecified OR **true**. |
| length must be greater than | 1 | no | The attribute length is less than or equal to the specified constant AND the optional condition is unspecified OR true. |
| length must be greater than or equal to | 1 | no | The attribute length is less than the specified constant AND the optional condition is unspecified OR true. |
| length must be less than | 1 | no | The attribute length is greater than or equal to the specified constant AND the optional condition is unspecified OR true. |
| length must be less than or equal to | 1 | no | The attribute length is greater than the specified constant AND the optional condition is unspecified OR true. |
| length must be equal to | 1 | no | The attribute length equals the specified constant AND the optional condition is unspecified OR true. |
| must be like | 1 | yes | The attribute matches the SQL LIKE-compliant constant or attribute parameter AND the optional condition is unspecified OR **true**. |

## Assignment Rule Operators

| Assertion | Parameters Required | Condition Required | Assignment Action |
| --- | --- | --- | --- |
| equals | 1 | no | The attribute is assigned a value equal to the specified constant or attribute parameter. |
| equals blank | none | no | The attribute is assigned a null value. |

If data quality rules are not applied as expected, check the **Event Log** for error information.

## See Also

[Create and Edit Validation Rule Clauses](https://support.profisee.com/wikis/profiseeplatform/create_and_edit_validation_rule_clauses)

[Create and Edit Assignment Rule Clauses](https://support.profisee.com/wikis/profiseeplatform/create_and_edit_assignment_rule_clauses)