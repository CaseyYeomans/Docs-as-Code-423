# Creating New Rules

Profisee Administrators can create new rules to be used in Profisee Portal from the **Quality** tab of the Administrator view in Portal. To create a new rule:

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ie92783c4056bbcdd.png)

1. Click the **+** icon from the Data Quality Rules toolbar.
2. Select an entity and attribute from the dropdown list. The created rule will apply only to the entity and attribute selected.
3. Click **OK**. A new rule is created in the Data Quality Rules grid.
4. Open the new rule to begin defining Validation Clauses and Assignment Clauses.![Image](https://profisee.visualstudio.com/ad098ab8-fc30-4fe4-982d-460e6c9eb694/_apis/wit/attachments/30d9a8c9-2948-4284-b16c-64efb2e4993f?fileName=image.png)

- **Validation clauses** validate existing values within an attribute. They are composed of one or more expressions, created using the Expression Editor. Clauses can have up to 10 conditions in the *Change to* and *When* fields. You can also click the **Constraint** checkbox next to a validation clause to make it a Constraint, which prevents users from creating or updating a record that violates that rule. See [here](https://support.profisee.com/wikis/profiseeplatform/create_and_edit_validation_rule_clauses) for more details.
- **Assignment clauses** set the value of an attribute when an optionally specified condition is true. They are composed of one or more expressions, created using the Expression Editor. See [here](https://support.profisee.com/wikis/profiseeplatform/create_and_edit_assignment_rule_clauses) for more details.
You can set one of three Execution Modes for assignment clauses to determine when that clause is run.
- Always
- On Create Only
- On Update Only
- If desired, click the **X** icon to the left of a clause to delete it from the rule or click the **X** to the right of an expression to delete just the expression. You can also click and drag clauses to reorder their execution within the rule.

5. Optionally, enter a **Display Description** that is displayed when a data quality issue is viewed by a user.
6. Click **Save** or **Save and Close** when you are finished creating the clauses.

- Note that you cannot create multiple rules for the same attribute. You must create multiple clauses under the same rule instead.

- Previously in rules hosted in FastApp Studio, you could assign a value in a DateTime attribute to a Date attribute. To do so now, you can use the expression: TODATE ( TEXT ( [DateTimeAttribute] ) )

- Previously in rules hosted in FastApp Studio, you could use the operators **Is valid** or **Is not valid** in validation rules.

To perform a similar function (prior to 2025 R4), you can use the clauses:
If: FALSE when: [Attribute] = NULL
If: TRUE when: [Attribute] <> NULL

To perform a similar function (in 2025 R4 or later), use "" in the expression instead of NULL.

- Previously in rules hosted in FastApp Studio, you could use the *Validation Status* value on a Parent record in a child entity data quality rule to see whether a rule was valid. To perform a similar function, create a user-defined attribute on a parent entity such as [Is Valid], then create an assignment rule on the parent entity that sets the [Is Valid] attribute to "Yes" if ValidationStatusID = 1 or "No" when ValidationStatusID = 2. Then change the rule on the child entity to reference the parent entity's [Is Valid] attribute. Since this is a user-defined attribute on the parent entity, it will be monitored for changes to the value and will invoke the dependent record processing.