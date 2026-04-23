# Using the Expression Editor in Portal

The expression editor allows you to create functional expressions to automatically perform specified actions when a strategy is added, updated, or deleted. Expressions can also be triggered manually in the Strategy tab.

The expression editor can be accessed from the Strategies tab to map properties for your connection strategy.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic19b0e4ceaa7fb5c.png)

To create an expression:

1. Navigate to the **Request** section of the **Strategies** tab on the portal administration page.
2. Hover over an attribute to expose the **Expression** icon--displayed as f(x)--next to an adjacent field to create an expression for the request.
3. Create an expression using the options given in the **Data Sources**, **Operators**, and **Functions** fields.

- **Data Sources**:This field allows you to select the attribute you wish to use as the subject for the expression.
- **Operators**: This field allows you to add modifiers to the expression such as NOT, <, or &. Operators set the conditions under which the expression functions.
- **Functions**: Functions allow you to give context to an expression with qualifiers such as TODAY, LEFT, or TEXT. Functions determine what happens to the attribute when the expression is performed. You can see additional details about what a function does by hovering over the information icon next to the function.

4. If desired, click **Verify** in the **Expression** field to confirm if the Expression is valid.
5. If desired, give the expression a **Display Description**to explain the purpose of the expression in plain text.
6. Click **Save** to save the function or **Cancel** to close the function without saving.

### Functions

| | | | | |
| --- | --- | --- | --- | --- |
| **Name** | **Function Description** | **Syntax** | **Parameter Descriptions** | **Allowed Values for Parameters** |
| **IN** | Compares whether an attribute value is in any one of the listed values or attribute's values. This function can be used to compare current, changed, or prior values. | Syntax: <attribute> IN (List of Value | <attribute> ) | **Attribute:** An attribute in your data model | **Attribute**: Attribute |
| **NOT IN** | Compares whether an attribute value is not in any one of the listed values or attribute's values. It can be used to compare current, changed, or prior values. | <attribute> NOT IN (List of Value | <attribute> ) | **Attribute**: An attribute in your data model | **Attribute**: Attribute |
| **DATEDIFF** | Calculates the number of days between start date and end date. | DATEDIFF( <startDate> , <endDate> ) | **startDate**: The start date. **endDate**: The end date. | **startDate**: Date, DateTime expression **endDate**: Date, DateTime expression |
| **TODAY** | Sets the value to today's date. | TODAY | - | - |
| **DATE** | Returns a Date expression for the values provided. | DATE( <DD> , <MM> , <YYYY> ) | **DD**: Day in DD format **MM**: Month in MM format **YYYY**: Year in YYYY format. | **DD**: Numeric expression **MM**: Numeric expression **YYYY**: Numeric Expression |
| **DATEADD** | Adds the corresponding day/month/year to a given Date expression. | DATEADD( <dateOrDateTimeExpression> , <numberToAdd> , <interval> ) | **dateOrDateTimeExpression**: Date or DateTime expression to augment **numberToAdd**: The number to add to a given Date expression **interval**: Date interval to add | **dateOrDateTimeExpression**: Date, DateTime expression **numberToAdd**: Numeric expression **interval**: Day, Month, Year |
| **RELATIVEDATE** | Calculates the relative date based on the Date or DateTime provided. | RELATIVEDATE( <givenDateOrDateTime> , <interval> ) | **givenDateOrDateTime**: Result will be a relative date of this Date or DateTime expression **interval**: Interval for calculating relative dates | **givenDateOrDateTime**: Date, DateTime expression **interval**: StartOfWeek, EndOfWeek, NextWeek, StartOfMonth, EndOfMonth, NextMonth, StartOfQuarter, EndOfQuarter, NextQuarter, StartOfYear, EndOfYear, NextYear |
| **NOW** | Sets the value to the current date and time. | NOW | - | - |
| **DATETIMEUTC** | Returns the date and time expression for the values provided. | DATETIMEUTC( <DD> , <MM> , <YYYY> , <HH> , <MM> , <SS> , <MS[optional]> ) | **DD**: Day (in DD format) **MM**: Month (in MM format) Allowed Values: Numeric expression **YYYY**: Year (in YYYY format) **HH**: Hour (in HH format) **SS**: Seconds (in SS format) **MS**: (Optional) Milliseconds (in MS format) | **DD**: Numeric expression **MM**: Numeric expression **YYYY**: Numeric expression **HH**: Numeric expression **SS**: Numeric expression **MS**: Numeric expression |
| **LENGTH** | Calculates the length of the string. | LENGTH( <stringExpression> ) | **stringExpression**: String expression to calculate the length of | **stringExpression**: String expression |
| **INDEXOF** | Finds the index of a given string expression within the specified string. | INDEXOF( <expressionToSearch> , <expressionToFind> ) | **expressionToSearch**: String expression in which you want to find the specified string **expressionToFind**: String expression to find | **expressionToSearch**: String expression **expressionToFind**: String expression |
| **CONTAINS** | Checks if a string contains a specified string. | CONTAINS( <expressionToSearch> , <expressionToFind> ) | **expressionToSearch**: String expression in which you want to find the specified string **expressionToFind**: String expression to find | **expressionToSearch**: String expression in which you want to find the specified string **expressionToFind**: String expression to find |
| **CONCAT** | Concatenates two or more strings. | CONCAT( <string1> , <string2> ) | **string1**: String expression to which you want to join other strings **string2**: One or more string expressions | **string1**: String expression **string2**: String expression |
| **LEFT** | Returns the specified number of characters in a given string from the left. | LEFT( <stringExpression> , <numberOfCharactersToReturn> ) | **stringExpression**: String expression from where you want to return characters **numberOfCharactersToReturn**: Number of characters to return | **stringExpression**: String expression **numberOfCharactersToReturn**: Numeric expression |
| **RIGHT** | Returns the specified number of characters in a given string from the right. | RIGHT( <stringExpression> , <numberOfCharactersToReturn> ) | **stringExpression**: String expression from where you want to return characters **numberOfCharactersToReturn**: Number of characters to return | **stringExpression**: String expression **numberOfCharactersToReturn**: Numeric expression |
| **SUBSTRING** | Returns a subset of a string from a given starting position to the end position. | SUBSTRING( <stringExpression> , <startPosition> , <endPosition> ) | **stringExpression**: String expression from where you want to return characters **startPosition**: Position of the first character **endPosition**: Position of the last character | **stringExpression**: String expression **startPosition**: String expression **endPosition**: Numeric expression |
| **TEXT** | Returns a string representation of a given expression. | TEXT( <anyExpression> ) | **anyExpression**: Date, DateTime, or Numeric expression that you want to convert into a string | **anyExpression**: Date expression, DateTime expression, Numeric expression |
| **NEWGUID** | Returns a new GUID string. | NEWGUID | - | - |
| **CHANGEDTO** | An attribute value has changed to any one of the listed values or attribute's values. | CHANGEDTO( <attribute> , (<List of Values | attribute>)) | **Attribute:** An attribute in your data model | **Attribute**: Attribute |
| **CHANGEDFROM** | An attribute value has changed from any of the listed values or attribute's values. | CHANGEDFROM( <attribute> , (<List of Values | attribute>)) | **Attribute:** An attribute in your data model | **Attribute**: Attribute |
| **PRIOR** | A reference to the attribute's prior value. The difference between the PRIOR and the CHANGEDFROM function is the PRIOR function does not test to see if the value changed. | PRIOR( <attribute> ) | **Attribute:** An attribute in your data model | **Attribute**: Attribute |
| **REGEX\***(2025.R4 and above) | Checks if a string contains a specified regular expression pattern. | REGEX(<expressionToSearch>, <patternExpressionToFind>) | **expressionToSearch**: String expression in which you want to find the specified string **patternExpressionToFind**: String regular expression pattern to match | **expressionToSearch**: String expression in which you want to find the specified string **patternExpressionToFind**: String regular expression pattern to matc |

*\*Note that this function is only available for users with SQL Server 2025 or higher OR Azure SQL. Users on older versions of SQL Server may be able to see this function, but it will not be functional.*

Though not currently included in the list of functions, NULL can be used in an expression to check for or assign blank values.

As an example: if you wanted to create a rule where Name is required, you could create the validation expression Name<>NULL, which would return a validation issue for any record without a value for Name.

Alternatively, if you wanted to create a rule where the Date field *must* be blank, you could create the validation expression Date=NULL.