# Manually Harmonize a Single Match Cluster Record

To manually harmonize one source record attribute value from the golden record:

1. Open a Matching Results view tab. For more information, see [Viewing matching results](https://support.profisee.com/wikis/profiseeplatform/view_matching_results).
2. Select a row in the main grid in order to display a match cluster in the bottom records grid.
3. Right-click the cell in the record that you want to overwrite with a value from the golden record.
4. Select **Harmonize this Value** on the menu.

The selected attribute value will be updated to match the value of the golden record.

The golden record must contain a value for the attribute before it can be harmonized. If a group does not have a golden record, you cannot promote or harmonize values for those group records. Run the survivorship portion of your strategy, either in batch mode or manually, to create golden records for any groups that do not have golden records.