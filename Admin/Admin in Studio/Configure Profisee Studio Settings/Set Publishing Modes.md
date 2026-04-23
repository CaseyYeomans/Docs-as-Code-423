# Set Publishing Modes

Profisee allows you to publish your entity grid changes in either live mode, in which your changes are saved immediately, or in deferred mode. Deferred mode is recommended and enabled by default because it offers the greatest flexibility (such as mass changes with undo and redo) and performance, as changes are published in bulk.

To use deferred mode:

1. Click **Settings** on the main toolbar.
2. Click **Desktop Settings** from the dropdown.
3. Select the **Entity** tab.
4. Select **Use deferred publishing mode for entity grid edits**. Clearing this option enables Live mode, which means every edit to an entity in Profisee is immediately published.
5. Change the batch size, if necessary.

The default size is 1000. Use a larger batch size if you usually perform mass edits. Use a smaller batch size if you usually edit only a few members at a time.

5. Select the Automatically add domain values option to add new domain values occurring in your pasted or imported data automatically.

When this option is cleared, new domain values are discarded.

Profisee switches you automatically to Deferred mode if you make changes to more than one cell at a time (including copy and paste). In Deferred mode, all changes are tracked by cell color indicators, delete row icons, and read-only status for deleted rows.

In Deferred mode, when you execute a large number of changes at once, Profisee publishes changes in batches.