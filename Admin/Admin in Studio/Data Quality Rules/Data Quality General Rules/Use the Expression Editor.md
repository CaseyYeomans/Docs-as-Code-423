# Use the Expression Editor

You can create powerful validation and assignment clauses with the use of the expression editor. The expression editor allows you to create free-form parameters to define the "What" portion of a data quality rule with a variety of attributes, operators, and functions.

## Open the Expression Editor

1. Navigate to the Data Quality Rules tab in Profisee FastApp Studio.
2. [Edit an existing data quality rule](https://support.profisee.com/wikis/profiseeplatform/edit_data_quality_rules) or [add a new data quality rule](https://support.profisee.com/wikis/profiseeplatform/add_data_quality_rules).
3. Edit or add a new Validation or Assignment clause.
4. Click the dropdown menu under the assertion column (the column with the attribute name) and select a compatible assertion.

The following assertions are not compatible with the expression editor: *is required, is valid, is not valid, must be blank.*

5. Click inside the parameter column (the column under **What**) to reveal the **f(x)** icon, then click the icon.

## Create an Expression

The expression editor uses several sources of information to create expressive parameters. Due to the free-form nature of creating expressions, you may use one, several, or none of each of the following inputs.

- **Attributes**: This field allows you to select any applicable attribute within the entity to use as a subject for your expression.
- **System Attributes**: This field allows you to select any applicable system attributes to define your expression. System attributes include **Created On**, **Created By**, **Last Updated On**, and **Last Updated By**. Note that for Assignment rules, only **Created On** and **Created By** are valid system attributes.
- **Operators**: This field allows you to add modifiers to the expression such as NOT, <, or &. Operators are organized as **Logical**, **Numeric**, and **String**.
- **Functions**: Functions allow you to give context to an expression with qualifiers such as TODAY, LEFT, or TEXT. Functions are organized as **Date And Time** or **String**.
- **Free-form Text**: You can manually enter information into the Expression field. Any free-form text must be expressed in double quotations. For example, the entry 38 is read as a numeric expression, but the entry "38" is read as text.

Double-click any attribute, operator, or function to add it to your expression.

The **Usage** field offers a brief description, proper syntax, and usage of the currently selected function.

The **Expression** field allows you to view and edit your expression as you develop it. You can place your cursor anywhere in an expression within the expression filed to mark where new attributes, operators, and functions are placed.

The **Verify** button allows you to check your expression for validity before applying it to the data quality rule. Selecting OK automatically verifies your expression. The Verify function can only determine whether or not your expression is valid and cannot detect specific errors in your expression. The validation process ensures the expression results in the date type the assertion is expecting. For example, "Must equal" will require the expression to match the data type of the rule attribute, but "Length must be equal to" always requires a number.

## Add an Expression to your Data Quality Rule

1. Open the Expression Editor within your desired validation or assignment.
2. Use the Expression Editor to formulate an expression as described above.

The datatype of the expression result must match the datatype of the attribute it modifies. For instance, a text attribute cannot be modified by a numeric expression. If the datatype of your expression and attribute do not match, the expression returns an error when verified. ![](https://Profisee.magentrixcloud.com/sys/StaticAsset/Read/file-i97ccd7b4da712e2a.png)

3. If desired, click **Verify** to ensure the validity of your expression.
4. Click **OK** to apply the expression.