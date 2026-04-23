# Apply Survivorship

When reviewing match groups in a Matching Results tab, you can run survivorship on individual groups with the **Apply Survivorship to Group** option. Apply Survivorship lets you create a golden record for a group that has no golden record (as for groups created when only the matching portion of a strategy has processed), or update promoted or harmonized values to take into consideration new or edited group records. This option is only available in Matching Results when the displayed results were produced for a strategy containing survivorship settings.

To apply survivorship to a match group:

1. Open a Matching Results tab.
2. In the top grid, select a record in the group to which you want to apply survivorship.

The group appears in the second grid.
3. Right-click anywhere inside the group.
4. Click Apply Survivorship to Group on the menu.

Survivorship is applied.

- If the group did not have a golden record, a golden record is created.
- If a record added to the group since survivorship last processed is a better source for promoting values, then those values are promoted.
- If applicable, harmonization is reapplied to group records.

Some conditions must be met in order to run survivorship from the Matching Results tab:

- Survivorship must be configured in the strategy
- The Survivorship option must be selected on the Strategy tab
- Match groups must exist
- The user applying survivorship must have sufficient rights to all affected records and attributes

Survivorship cannot be applied to:

- Excluded or unmatched records
- Records with a match status of Unique when the strategy is not configured to create golden records for unique records

Survivorship is applied automatically when the strategy contains survivorship, and:

- A record is made unique and the strategy creates golden records for unique records
- A new group is created