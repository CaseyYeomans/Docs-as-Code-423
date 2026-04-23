# Build an Entity Grid Filter

The entity grid filter makes it possible to build a filter for one or multiple attributes.

To build an entity filter:

1. Click **Filter**.

The Filter and Sort dialog appears.
2. Do one of the following:

- Open the **Attribute** list and then select an attribute.
- **--or--**
- Click the ellipsis button (...) and then select an attribute from the **Multilevel Attribute Selector**. Click **OK** to add the selected attribute to the filter.

The Multilevel Attribute Selector lets you select parent attributes in addition to attributes in the entity.

- **Parent attributes**: DBAs in the entity provide links to the entities which are domains for those DBAs. Other attributes (parent attributes) in those entities can also be used as filter criteria. You can browse for parent attributes using the tree provided, expanding the entity and choosing the attributes from the list. When you select parent attributes, you are filtering the entity based on the values for the parent entity attribute. For more information, see [Filtering using parent attributes](https://support.profisee.com/wikis/profiseeplatform/filter_using_parent_attributes).
3. In the **Operator** column, select the operator to use from the list.

Choose from the following operators:

| Operator | Function | SQL Equivalent |
| --- | --- | --- |
| is blank | A value for the attribute is not present | = |
| is not blank | A value for the attribute is present | != |
| equals | Equals | =" OR ... IS NULL |
| does not equal | Does not equal | !=" AND ... IS NOT NULL |
| is less than | Less than | < |
| is less than or equal to | Less than or equal to | <= |
| is greater than | Greater than | > |
| is greater than or equal to | Greater than or equal to | >= |
| contains | The attribute value contains the specified string | LIKE '%x%'' |
| does not contain | The attribute value does not contain the string | NOT LIKE '%x%' |
| contains the pattern | The attribute value contains the specified pattern (requires SQL LIKE pattern) For more information on SQL LIKE patterns, see [https://msdn.microsoft.com/en-us/library/ms179859.aspx](https://msdn.microsoft.com/en-us/library/ms179859.aspx "https://msdn.microsoft.com/en-us/library/ms179859.aspx") | LIKE 'x' |
| does not contain the pattern | The attribute value does not contain the specified string (requires SQL LIKE pattern) For more information on SQL LIKE patterns, see [https://msdn.microsoft.com/en-us/library/ms179859.aspx](https://msdn.microsoft.com/en-us/library/ms179859.aspx "https://msdn.microsoft.com/en-us/library/ms179859.aspx") | NOT LIKE 'x' |
| starts with | The attribute value starts with the specified string | LIKE 'x%' |
| does not start with | The attribute value does not start with the specified string | NOT LIKE '%x%' |
| ends with | The attribute value contains the string at the end of the value | LIKE '%x' |
| does not end with | The attribute value does not contain the string at the end of the value | NOT LIKE '%x' |
| is between | The attribute value is between the two entered values | BETWEEN x AND y |
4. In the Value column, enter the value to use with the filter.

When using the is between operator, you must enter a value in each of the two fields provided.

An attribute can also be a value. Select an attribute to compare to the attribute in the Attribute field by clicking the ellipsis button to the right of the Value field. You may need to click inside the Value field to get the button to appear.
5. To add additional lines for more filter conditions, click **Insert**.

You can group together filtering statements as well as add AND and OR logic to your filter. For more information, see [Multi-line entity grid filters](https://support.profisee.com/wikis/profiseeplatform/multi_line_entity_grid_filters).
6. Click **Save** to save the filter and exit the Filter and Sort dialog.

The entity grid reloads with the filter settings applied.

The currently applied filter, expressed as a Transact-SQL statement, displays at the bottom of the Filter and Sort dialog while you are editing the filter. It also displays above the entity grid, beside the **Filter** button.

For operators requiring no value (**is blank** and **is not blank**), there is no option for Value. NULL values are treated as blanks.

To filter for blank values, you must use the **is blank** operator. **Equals** requires a value.

Available operators are based on the attribute data type. If an operator is not valid for a data type (for example, greater than for a link attribute), then that operator does not display in the list.

Hovering over the Filter icon displays all filtering information currently applied to the grid, including search criteria, sorting information, and current filters.