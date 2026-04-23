# Start, Stop and Pause Event Processing

The Real-Time Event Processing tab includes controls for stopping, starting, and pausing event processing within the Profisee cluster. These actions control event processing for the entire cluster.

The displayed text above the control buttons indicates the current state of the event processing engine. Buttons appear gray when they are associated with actions that are irrelevant for the current state. For example, you cannot click Pause when event processing is stopped or already paused.

## Pausing vs. Stopping

While event processing is paused, the event publishing server continues queuing up events for processing by the event consuming server. When event processing is started again from a paused state, processing automatically picks up from the point where it was paused.

When event processing is stopped, all events that occur while event processing is stopped are discarded.

## Start Event Processing

To start processing events when event processing is stopped:

1. Click **Start**.

The Start Event Processing dialog appears.
2. Select how to begin processing events:

**--or--**

Profisee begins processing events

- **The first transaction**

Begins processing with the first transaction found in the queue.
- **Right now**

Begins processing with the first transaction added to the queue after event processing is enabled.

The Start options dialog only appears if events are being processed on this system for the first time. If you are starting event processing after stopping it, then no options are presented--events are queued and processed from that point forward.

## Stopping Event Processing

To stop event processing:

1. Click **Stop**.

The Stop Event Processing dialog appears.
2. Select an option in the dialog:

**--or--**

- **Stop event processing**

Event processing stops. If processing was previously paused, any queued events are discarded when the event processing engine is restarted. Additional events are not added to the queue while processing is stopped.
- **Do not stop event processing**

Event processing continues. Selecting this option cancels the action, and event processing continues to run.

Event processing does not stop immediately when Stop is clicked. Instead, it finishes processing the current transaction event. This ensures that the event currently processing completes before the engine stops.

- If event publishing is underway, Profisee waits until publishing finishes, and then stops event processing.
- If event consuming is underway, Profisee waits until the events in that range are processed before event processing stops.

## Pausing Event Processing

To pause event processing:

1. Click **Pause**.

The Pause Event Processing dialog appears.
2. Select an option in the dialog:

- **Pause event processing**

Event processing pauses. Events continue to queue. When event processing resumes from a paused state, processing automatically picks up from the point where it left off (the last transaction checkpoint).

**--or--**

- **Do not pause event processing**

Event processing continues. Selecting this option cancels the action, and event processing continues to run.