# Delete a Scenario

To delete a scenario:

1. In the navigation pane, under Administration, click **Real-Time Event Processing**.
2. On the Real-Time Event Processing tab, click **Stop**.
3. On the Stop Event Processing pop-up, click **Stop event processing**.

You must stop event processing before you change or delete any event processing component configurations.

4. On the Real-Time Event Processing tab, click **Profisee event scenarios and subscriptions** to delete a Profisee event scenario, or External event scenarios and subscriptions to delete an external event scenario.
5. Select the event scenario in the list.
6. Click **Delete**.

**IMPORTANT**: When you delete an event scenario, all event messages associated with the scenario are also deleted, regardless of processing status.
7. Click **Yes** in the pop-up to confirm the deletion.
8. If any event messages are associated with the scenario, you must confirm that you want to delete them. Click Yes in the **Delete Event Scenario** dialog to confirm.

The event scenario is removed from the list.

The event scenario is not actually deleted immediately, even though it is immediately removed from the list. Instead, it is assigned a status of **pending delete** and assigned a new globally unique identifier (GUID). The next time the housekeeping service processes purge requests, the event scenario will be purged from the system. The event messages associated with the scenario are also deleted at this time.

Because the scenario is assigned a new GUID when it is deleted, you can recreate it immediately after deleting it by importing a previously exported copy of it.

For more information on housekeeping, see [Housekeeping](https://support.profisee.com/wikis/profiseeplatform/housekeeping_overview). For more information on statuses, see [Real-Time Event Processing components status](https://support.profisee.com/wikis/profiseeplatform/real_time_event_processing_components_status).