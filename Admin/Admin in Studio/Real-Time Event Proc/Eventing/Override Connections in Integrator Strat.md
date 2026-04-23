# Override Connections in Integrator Strategies

The Profisee connection used in Integrator strategies can differ from the server defined in the subscriber configuration. Profisee uses a process of overriding connections in data transfer strategies to simplify the configuration process. This makes it possible to use a single strategy on multiple systems without editing it with Integrator (formerly Federation Manager) for each server environment in which it will run.

Connection overriding occurs according to the following rules:

- If one connection in the data transfer strategy is a Profisee connection (either source or target), then the current Profisee server connection replaces the Profisee connection in the strategy.
- If both connections in the data transfer strategy are Profisee connections, but the connection strings are different, then the current server replaces the source Profisee system in the strategy.
- If both connections in the data transfer strategy are Profisee connections, and the connection strings for both the source and target servers are exactly the same, then the current Profisee server replaces both connections in the strategy.