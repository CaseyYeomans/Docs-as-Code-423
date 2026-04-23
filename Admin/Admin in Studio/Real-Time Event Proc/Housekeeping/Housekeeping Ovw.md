# Housekeeping Overview

##

Profisee housekeeping is a process configured through Profisee System settings that can be scheduled to run periodically using a task scheduler. Currently, it is only applicable to event processing, and it has two functions:

- To remove expired event messages

Removing old event messages helps to limit disk utilization and maintain optimal performance during event processing.
- To remove deleted subscriptions, event scenarios, and subscriber configurations

Event configuration components--subscriptions, scenarios and subscriber configurations--cannot be deleted until all events related to them are deleted. Housekeeping provides the ability to delete these components after all related events have been purged.

## Event Messages

Whenever Profisee Server publishes an event message, that message persists until it is purged. Without oversight, the data tables storing outbound (Profisee) and inbound (external) events continue to grow and, left unchecked, they can eventually impact disk space and event processing performance, as well as other Profisee database-dependent services in the server environment.

Housekeeping limits subscription event queue growth automatically by controlling the number of event messages stored in data tables. It does this by flagging event messages to be purged when they exceed the retention threshold age defined in Profisee System Settings under Housekeeping. When housekeeping runs, the expired messages are removed.

## Event Processing Components

Subscriptions and event scenarios used in event processing contain dependencies that can make deleting them a complex task. Housekeeping makes it possible for administrators to delete the components of event processing without needing to take these dependencies into account. The deleted items are flagged for deletion, along with any event messages associated with a deleted subscription, scenario, or subscriber configuration. Housekeeping completes the removals in the background, reducing the number of steps required and making the process fast and transparent to the administrator.