# Paste

Paste into the Profisee entity grid from the clipboard. Copy sources include most applications that store data in a tabular format.

1. Copy data to the clipboard. For more information, see [Copy](https://support.profisee.com/wikis/profiseeplatform/Copy).
2. In the entity grid, select the paste range.
3. Right-click inside the selected range.
4. Click **Paste** on the menu.

Data is pasted into the selected range.

When auto-extend or data conversion is required:

- Profisee supports pasting into all cell types except read-only cells, incompatible format paste (for example, text data into a link cell), free-form attribute number or date into domain-based attribute cells, number or date incompatible cells.
- If you attempt to paste data of one type into an attribute of a different type, the pasted data type may be converted.
- When data is pasted into a domain-based attribute column, Profisee attempts to convert the data type even when the pasted data is incompatible with destination cells.
- When you paste a new value into a domain-based attribute column, the value is added to the source domain entity if **Automatically add domain values** is selected under Desktop Settings for Publishing. Otherwise, the new values (values not found within the source domain) are discarded during publishing.
- Pasted values in DBA columns are matched to existing domain values based codes of the domain members and the currently selected display format.

Restrictions on pasting:

- You must select as your paste destination at least as many horizontal and vertical cells as you copied. For example, you cannot copy a data range that is four cells wide and four cells long into a range that is two cells wide and three cells long. Otherwise, an error displays.
- When you use paste append to add data to the entity grid, the grid automatically adds additional rows to hold the new data.
- When you attempt to paste an incompatible data type into the grid, an error displays. For example, this occurs when you attempt to paste numeric data into a date attribute. In cases when data type conversion is not possible, the target cells will retain the original values and formatting and the paste will fail.
- When pasting into Profisee, the member grid display of Code and Name must match the source data. For instance, if Profisee display is set to Code{Name}, then the source data must either be formatted in this way or contain Code only. The Code Name Separator must also be the same.