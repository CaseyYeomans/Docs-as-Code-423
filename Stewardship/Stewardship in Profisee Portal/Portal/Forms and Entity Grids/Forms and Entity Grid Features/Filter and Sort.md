# Filter and Sort

Profisee Portal users can use the Filter and Sort option to get attributes for their entity based on a set of criteria. The Filter and Sort dialogue is accessible through the **Filter/Sort** icon in an Entity Grid toolbar.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i97947c902c2da421.png)

### Custom Filter

The **Custom Filter** tab allows you to filter your data based on a set of expressions.

The **Expression Builder** allows you to create expressions using **Attributes**, **Operators**, and **Values**.

- **Attribute**: The attribute within the entity you want to filter
- **Operator**: A set of conditions by which to filter your attribute (Contains, is greater than, is between, etc.)
- **Value**: A plaintext field to set the value for your operator
- **And/Or**: Determines if additional expressions are And'd or Or'd (only appears on secondary expressions)

A completed expression may resemble: Cost (attribute) is greater than (operator) $15 (value).

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-idde7a244257279f2.png)The Custom Filter also includes a toolbar that allows you to edit your expressions. These tools include the following:
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i1ad176c68710b95d.png)

- **Add**: Adds a blank secondary expression to the Expression Builder
- **Delete**: Deletes a selected secondary expression
- **Move up**: Moves the selected expression(s) one row higher
- **Move down**: Moves the selected expression(s) one row lower
- **Group**: Groups two or more selected expressions (shift + click to select multiple). Grouped expressions are treated as a single expression when being moved or deleted.
- **Ungroup**: Returns a grouped expression to individual expressions
- **Delete all**: Deletes all expressions

Once all expressions have been created, click **Save** to filter the entity grid based on your selections.

### Sort

The **Sort** tab allows you to order attributes by alphabetical or numeric order (based on the configuration of the attribute).![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i74d951469faedbe5.png)

To sort the entity grid:

1. Select an attribute in the **Attribute** field you wish to sort by.
2. Click the **Direction** dropdown and select Ascending or Descending.
3. If desired, click the **Add**icon to add an additional attribute to sort by. Attributes higher in the list have higher sort priority.

Click **Save** to sort the entity grid based on your selections.

### See more

[Using the Quick Filter](https://support.profisee.com/wikis/profiseeplatform/use_the_quick_filter)