# Retry Failed Messages

When the event consuming server attempts to pass a notification message to the subscriber, issues can occur. Connectivity issues can prevent the message from reaching the subscriber, or configuration issues could cause the subscriber to return an error.

Message failures are reported on the event processing dashboards, in the Failed Messages panel. External events are recorded on the External Events Dashboard, and Profisee events are recorded on the Profisee Events Dashboard. In both cases, reporting and retrying is handled the same way. Failed messages are not discarded, so you can retry them later on when the issue is fixed, and whatever processing that should have occurred happens.

After the problem causing the failure is fixed, you can retry the failed messages by doing the following:

The failed messages are processed according to your selection.

1. In the navigation panel, click **Real-Time Event Processing**, under Administration.
2. On the Real-Time Event Processing tab, click **Profisee Events Dashboard** for Profisee events, or click **External Events Dashboard** for external events.

The selected dashboard tab displays.
3. In the Queued Messages panel, click **Expand** to open the panel to the full width of the tab.
4. In the Data column, under Subscriptions, select the subscription.
5. Click **Errors**.
6. Select one of the options:
- **Retry one**

Retries the first message associated with this subscription that failed. Use this option when checking to see if an issue with event processing has been resolved.
- **Retry all**

Retries all failed messages associated with this subscription. Use this option when you are certain that the issue causing the failed messages is resolved. Otherwise, all of the failed messages will fail again.
- **Ignore all**

Use this option to skip processing the failed messages for this subscription. Use this option when the failed messages are unimportant, as during testing.