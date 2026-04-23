# Best Practices for Event Processing

- When event processing tasks are running, stop and restart event processing to force the event processing cache to use the new settings whenever changes are made to subscriber configurations and event scenarios.
- Use event processing to synchronize systems with a relatively low volume of changes.
- Use Profisee Integrator (formerly Federation Manager) to perform large data loads for application data transfers.
- Use care when using data service strategies with event processing, as numerous automated calls to data service providers can result in unanticipated charges. Profisee recommends that you always include a filter in data service strategies. Refer to the Integrator documentation for more information.
- If a single request triggers more than 1000 events, it should be treated as a batch and not used with real-time event processing. Instead, consider using one of the batch features such as Staging or the REST API in this scenario.