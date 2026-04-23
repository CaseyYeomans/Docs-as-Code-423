# Eventing FAQ

The following are answers to frequently asked questions about eventing administration:

- How can I tell when my event should be completed?

An event is triggered after the data transaction is processed by the audit service (the meta.tdatatransaction, auditenddtm is not null). After the event is triggered, it will display on the eventing dashboard as **Queued**.

Events are processed by the event subscriber in order. Once processed, it will display as P**rocessed** on the eventing dashboard.

- Some events display with an **Error** status. How can I fix this?

The error is logged to the **logging.tsystemlog** table. You can also see the error in the **meta.tEventMaestroMessageSubscriberErrors** table. Correct the error and try the event again from the dashboard.

Examples that would cause errors include "required constraint value is missing" or "missing DBA value."

- I have event messages that are stuck in the **Queued** state. How can I fix this?

Submit another change to try to 'un-stick' the message in the queue. If that fails, you can manually change the status in **meta.tEventMaestroMessageSubscriber** from 1 (queued) to 2 (processing).

- Why are my events not being picked up after restarting the service?

Eventing will begin to pick up **Queued** events when the next change is manually submitted OR when the system setting **Background transaction monitor interval timer** has elapsed. This setting is set to 60 minutes by default.

- My external events are not triggering. How can I troubleshoot this?

Set the logging level to **Information** in the monolith (this requires an IIS reset and service restart). Make sure that Eventing is on and resend the external event. You should see a message resembling the following:

WSRENE01.corp.profisee.com: Eventing Audit Message - External event criteria miss: Entity: contact, Member: 10029, ChangeType: Delete, Tag: 1, SystemInstanceName: 1

**Tips**:
-Make sure that entity name specified in external event scenario exactly matches what is sent (this may be case sensitive).
-If triggering based on changed attributes, ensure the attribute names specified in the external event scenario exactly matches what is sent (this may be case sensitive).
-If using Tags, ensure the tag specified in the external event scenario matches what is sent.
-Make sure the **ChangeType** above matches what you have configured.
-Make sure the system name above matches what you have configured.
-If you do not see the event, ensure your external system is correctly configured to send the events.

- What is the function of the *meta.tdatatransaction* table?

When data is changed in Profisee, a record is added to the *meta.tDataTransaction* table.The type of transaction is stored in the *ChangeTypeID* column based on the sending API.

These ChangeTypeID values are:
1 = create
2 = update
3 = delete
4 = merge\*
5 = Member Annotation (this means file attachment was modified)
6 = Annotation attribute (currently unused)
7 = Logging Turned On
\*The Merge API (equates to REST Patch request with IsUpsert=True) can resolve to either a *create* or an *update*. To determine which type of transaction occurred, you must correlate this with the history table for that *transactionid* to see if the merge was a create or update (the history table also has a ChangeTypeID column).

After Audit has processed the transaction, the *MemberCount* column is updated to show the number of records included in the transaction. Eventing will wait until Audit is complete (AuditEndDTM is not null) to process the transaction.

- Why didn't my subscriber run as expected?

Make sure eventing is turned on.

Make sure your subscriber configuration is linked to an even scenario and is enabled.

Make sure your subscriber configuration is correcly defined on the **Properties** tab.

- Why are there missing/skipped IDs in my transaction table?

If an update is triggered that does not result in any data being changed, that transaction will not be logged, but the ID will effectively be "used." Skipped IDs do not indicate an issue with your environment, only that a transaction that did not change your data was triggered.