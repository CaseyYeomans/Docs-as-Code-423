# Delete a Subscriber Configuration

To delete a subscriber configuration:

1. In the navigation pane, under Administration, click **Real-Time Event Processing**.
2. On the Real-Time Event Processing tab, click **Stop**.
3. On the Stop Event Processing pop-up, click **Stop event processing**.

You must stop event processing before you change or delete any event processing component configurations.

1. On the Real-Time Event Processing tab, click **Subscriber configurations**.
2. On the Subscriber Configurations tab, select the subscriber configuration in the list.
3. Click **Delete**.

**IMPORTANT**: When you delete a subscriber configuration, all event messages associated with scenarios linked to the subscriber configuration are also deleted, regardless of processing status.
4. Click **Yes** in the pop-up to confirm the deletion.
5. If any event messages are associated with the subscriber configuration, you must confirm that you want to delete them. Click **Yes** in the **Delete Subscriber Configuration** dialog.

The subscriber configuration is removed from the list.

The subscriber configuration is not actually deleted immediately, even though it is immediately removed from the list. Instead, it is assigned a status of **pending delete** and assigned a new globally unique identifier (GUID). The next time the Housekeeping service processes purge requests, the subscriber configuration will be purged from the system. Any event messages associated with the subscriber configuration are also deleted. If multiple scenarios are linked to the subscriber configuration, then the messages associated with each scenario are purged in separate purge requests.

Because the subscriber configuration is assigned a new GUID when it is deleted, you can recreate it immediately after deleting it by importing a previously exported copy of it.

For more information on Housekeeping, see [Housekeeping](https://support.profisee.com/wikis/profiseeplatform/housekeeping_overview). For more information on statuses, see [Statuses of Real-Time Event Processing components](https://support.profisee.com/wikis/profiseeplatform/real_time_event_processing_components_status).