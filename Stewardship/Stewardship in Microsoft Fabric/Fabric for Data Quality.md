# Using Fabric for Data Quality

Data Quality Rules allow you to specify criteria for an attribute and flag that attribute if the criteria is not met. For example, a rule with a specified clause "Cost must be greater than $10" will trigger if an attribute has a Cost value of less than 10. You can manage Data Quality Rules inside Microsoft Fabric, allowing you to create, remove, and edit rules and persist those changes into Profisee.

## Creating Rules in Fabric

To create rules in Microsoft Fabric:

1. Open a workspace for a data product that has at least one entity and attribute.
2. Click the Quality tab under the explorer. If any rules have already been created, they will display here.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i4dc0472433c6d7c5.png)
3. Click the **+** icon on the toolbar to open the **Create new rule** pane.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i7df6c6737226f037.png)
4. Select an entity and attribute to which the rule will apply, then click **Ok**.![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i74b3abf7dbc432e0.png)
5. A new rule with no clauses is created and added to the list of rules.

## Adding clauses to a rule

Clauses must be added to a rule to cause it to flag or alter attributes that meet the conditions of the clause. There are two kinds of clauses that can be added to a rule:

- **Validation Clauses** notify users when an attribute value triggers a specified condition.
- **Assignment Clauses** set the value of an attribute when a specified condition is true.

To add a clause to a rule:

1. Right-click a rule from the Quality list in Fabric, then click **Open.**![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i1d83fb5302f73973.jpeg)
2. Select the **Validations** or **Assignments** tab depending on the type of clause you wish to create.
3. For Validation Clauses:![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ie6eba89d52a088e1.jpeg)
1. Click **Add** below the **Validation Clauses empty** pane (if empty) or **+ Add** from the clause pane if one or more clauses already exist.
2. Click the **Valid if** field to build a clause using the [Expression Editor](https://support.profisee.com/wikis/profiseeplatform/using_the_expression_editor_in_portal) and define the conditions for this clause.
3. Select the **When** field to define when the clause should be applied. This is defined with a second expression.
4. Select the **Constraint** checkbox if you wish to make the clause a constraint. Constraint rules prevent users from creating or updating a record that violates that rule.
5. Click **Save** or **Save and Close** when you are finished to create the clause.
4. For Assignment Clauses:![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i807cbf9152a6c288.png)
1. Click **Add** below the **Assignment Clauses empty** pane (if empty) or **+ Add** from the clause pane if one or more clauses already exist.
2. Select the **Execution Mode** for this clause.
- **Always**runs rules on all members regardless of type.
- **On Create Only** runs rules on newly created members.
- **On Update and on Demand** runs rules when a member is updated through interactive updates (this can be editing on the portal, on the entity grid, etc.) or staging, and when rules are run on demand for the whole entity.
3. Click the **Change to** field to build a clause using the [Expression Editor](https://support.profisee.com/wikis/profiseeplatform/using_the_expression_editor_in_portal) and define the conditions for this clause.
4. Select the **When** field to define when the clause should be applied. This is defined with a second expression.
5. Click **Save** or **Save and Close** when you are finished to create the clause.