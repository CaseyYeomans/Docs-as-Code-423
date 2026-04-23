# Unregister a Subscriber

To unregister a subscriber:

1. In the navigation pane, under Administration, click **Real-Time Event Processing**.
2. On the Real-Time Event Processing tab, click **Stop**.
3. On the Stop Event Processing pop-up, click **Stop event processing**.

You must stop event processing before you change or delete any event processing components.

1. On the Real-Time Event Processing tab, click **Subscribers**.
2. Select the subscriber in the **Registered Subscribers** pane.
3. Click the left arrow to move the selected subscriber to the **Available Subscribers** pane.

- If no events are associated with the subscriber, then it is removed from the list.
- If there are events associated with the subscriber:

1. Remove any subscriber configurations linked to the subscriber in subscriptions:
1. On the Real-Time Event Processing tab, click **Profisee event scenarios and subscriptions** (to edit a Profisee event subscription) or **External event scenarios and subscriptions** (to edit an external event subscription).
2. On the Event Scenarios tab, select a subscription, and then click **Edit**.
3. Click the **Subscriptions** tab.
4. Select the subscriber configuration in the Selected subscriber configurations pane, and then click the left arrow.
5. Click **Save and Close**.
2. Delete any subscriber configurations linked to the subscriber. For more information, see [Deleting a subscriber configuration](https://support.profisee.com/wikis/profiseeplatform/delete_a_subscriber_configuration).
3. Wait for housekeeping to purge messages associated with deleted components.
4. Unregister the subscriber.