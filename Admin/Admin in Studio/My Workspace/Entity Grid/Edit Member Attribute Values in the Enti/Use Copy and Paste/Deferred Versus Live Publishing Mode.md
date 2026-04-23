# Deferred Versus Live Publishing Mode

All changes made in Profisee must be published to the Profisee Server to save the new data. You can use deferred publishing, which causes Profisee to wait to publish until you click **Publish**, or you can use live mode, which immediately publishes every change you make.

When you perform mass updates, Profisee operates in deferred publishing mode to maintain control over inadvertent changes and highlight pending changes as you go. When you make individual changes, you can operate in live mode to publish your changes immediately as you edit.

## Setting Publishing Modes

1. Click **Settings** in the main toolbar.
2. In the General tab, select **Grid Deferred Publishing** to use Deferred publishing mode, or clear this option to use live mode.

Profisee switches you automatically to deferred mode if you attempt any changes across more than one cell (including copy and paste). In deferred mode, all changes are tracked by cell color indicators, delete row icons, and read-only status for deleted rows.

In deferred mode, when you execute a large number of changes at once, Profisee publishes changes in batches and communicates publishing status in terms of batches completed.