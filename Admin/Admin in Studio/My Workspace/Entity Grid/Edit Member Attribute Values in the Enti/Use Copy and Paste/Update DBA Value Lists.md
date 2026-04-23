# Update DBA Value Lists

Lists of values for domain-based attributes (DBA) rarely change in many environments. For this reason, Profisee gets a list of DBA values the first time the attribute is accessed in a Profisee session. These values are then cached to improve performance. If you and other users add new domain values, or change those values, in concurrent Profisee sessions, you can both change the domain values and see these new updated values in domain member lists by adjusting the following settings.

## Always Check for Changes to Lists of DBA Values

If domain values are frequently added in your Profisee environment, select Always check for changes. When this option is selected, Profisee checks for updates to lists of values every time a DBA list is clicked. If updated values are found, Profisee updates the list. This setting is useful if you want to make sure you are using the most current lists of domain values possible.

1. Click **Settings** in the main toolbar.
2. On the Entity tab, select the **Always check for changes** option under Domain Attributes.
3. Click **Save**.

## Update DBA Values List From Within the Grid

To add DBA values using the entity grid:

1. Copy the new DBA value from an external source or from another cell to the clipboard.
2. Select the cell where you want to add a new DBA value.

Make sure you select the entire cell and not the cell contents. Profisee will simply search for the text you type if you have activated the DBA list.
3. Paste the value into the cell.
4. If you have selected **Automatically add domain values** under Profisee Settings, then Profisee adds the new value to the DBA when you publish to Profisee. If you have not selected this option, then new DBA values will be discarded.

You must have Update and Create permission on the domain entity to add values.