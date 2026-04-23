# Real-Time Event Processing Components Status

Subscriber configurations, scenarios and subscriptions display one of four statuses. Some of these statuses are indicated by informational icons in the relevant tab under Real-Time Event Processing, while others can only be viewed by directly querying the Profisee database. Active components display no icon, and components with a status of Delete Pending do not display at all because they have been removed.

To view the statuses of all event processing components, execute the following query:

SELECT \* FROM prof.viw\_SYSTEM\_SCHEMA\_EVENT\_SUBSCRIPTIONS

| Component Status | Loaded in cache? | Icon Displayed | Status Description |
| --- | --- | --- | --- |
| **Active** | Yes | none | The component is valid. It may or may not be in use. |
| **Unloaded** | No | | The event processing service failed to load the component because of a severe error. |
| **Delete Pending** | No | none | The component was unloaded from the event processing service cache and is currently disabled. |

When the event processing service is stopped, then the event processing cache is unloaded, and no components are loaded.