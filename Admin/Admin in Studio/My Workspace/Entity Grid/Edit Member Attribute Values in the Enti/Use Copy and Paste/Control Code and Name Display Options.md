# Control Code and Name Display Options

In the entity view, you can control how a referenced member is displayed and identified in a domain-based attribute cell.

## Changing the Entity Grid Member Display Option

Control the display of the Code and Name values for domain-based attributes by selecting one of the following options from the list in the entity grid toolbar:

- Code: displays only the code of the referenced member
- Code{Name}: displays the code followed by the name in braces
- Name{Code}: displays the name followed by the code in braces

The above options also determine how the domain attribute lists are sorted. If **Code** or **Code{Name}** is selected, the column values will be sorted by code. If **Name{Code}** is selected, the column values will be sorted by name.

## Changing Default Code and Name Separator Symbols

1. Click **Settings** on the main toolbar.
2. On the General tab, click the **Code Name Separator** list.
3. Select the formatting for code and name that you want to display in the entity grid. Available options are:
- ... {...}
- ... [...]
- ... |...|
- ... $...$
- ... #...#
- ... @...@
- ... ^...^
4. Click **Save**.
5. Click **Refresh** on the entity grid toolbar.

Domain-based attributes display with the selected separators. All subsequent entities that you open in Profisee will display Code and Name according to this selection.