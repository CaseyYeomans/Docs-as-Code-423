# Event Processing Elements

### Subscriber

A subscriber is a DLL file that is installed on the event consuming server in a Profisee cluster. When a triggering event occurs, the subscriber receives a notification message from the event consumer. The subscriber then performs the action (starting a workflow, transferring data, or other function) it is designed and configured to perform, using strategies and other settings defined in the subscriber configuration. Subscribers are available from Profisee, or your organization can develop specialized subscribers using the Software Developers Kit (SDK).

A Profisee cluster can have multiple subscribers, and a subscriber can have multiple configurations that perform different types of transfers.

Profisee currently offers three different subscribers:

- Data Transfer Controller

Provides functionality for data transfers between Profisee and other systems. Connector files, which are licensed separately, are also necessary to use this subscriber.
- Data Service Controller

Provides functionality for data service calls between Profisee and Web-based data service providers. Connector files, which are licensed separately, are also necessary to use this subscriber.
- MSMQ

Provides event-based functionality for queue-based flows
- TextWriter

Uses events to trigger writing to a file. This subscriber is most commonly used for testing.

### Connector

Connectors are DLL files that are specific to particular application servers (like Salesforce and Dynamics CRM) and data service providers (like Dun & Bradstreet and Melissa Data).

Connectors work in conjunction with the Data Transfer Controller (for application data transfer connectors) and the Data Service Controller (for data service call connectors) subscribers, making communication with other systems possible. The connector are files located under the Subscribers folder. There are no connectors installed with Profisee. You must copy all files and folders under the Integrator Subscribers folder to the Profisee Subscribers folder when you install connectors in Profisee for the first time. To upgrade or install individual connectors, follow the instructions included in the documentation for that connector.

To create a subscription using an Integrator strategy, you first must install the connector included in the strategy on the event consuming server.

For more information, see [Installing Subscribers on the Event Consuming Server](https://support.profisee.com/wikis/profiseeplatform/install_subscribers).

### Subscriber Configuration

A subscriber configuration includes the name, context, and the user-editable options available for this instance of the subscriber (like a strategy file). Subscriber configurations add the information necessary for the subscriber to transfer data (or perform other work defined in the subscriber) between systems. A subscriber configuration is called a subscription after it is linked to a scenario.

### Scenario

A scenario defines the possible circumstances (events logged transactions in the transaction table) that can cause a triggering event.

### External Event Scenario

External event scenarios are data changes which occur on systems outside of a Profisee cluster that cause a triggering event in Profisee event processing.

### Internal Event Scenario

Internal event scenarios are sets of event conditions defined for a Profisee cluster that trigger event processing.

### Event Consuming Server

A Profisee cluster can include one or more *event consuming servers*. A Profisee cluster that performs event processing must have at least one event consuming server. Event consuming servers process the events which have been queued up by the event publishing server. The event consuming server passes a notification event to the subscriber, indicating that an event corresponding to a predefined scenario has occurred, and that the associated subscription should be applied.

### Event Publisher

A Profisee cluster configured for event processing must contain a single Profisee server with the *event publishing* role. The event publishing server monitors events in the transaction table and checks to see if they match configured scenarios. Matching events are queued up for the event consuming server to process.

### Data Transfer Strategy

*Data transfer strategies* are created using Profisee (R) Integrator (formerly Federation Manager) and are required for subscriber configurations for the Data Transfer Controller subscriber. Data transfer strategies locate the source and destination servers, and control where incoming data is written, and restrict data transfers to specific types. Strategies can also limit the data transferred with filters.

### Data Service Strategy

*Data service strategies* are created using Profisee (R) Integrator (formerly Federation Manager) and are required for subscriber configurations for the Data Service Controller subscriber. Data service strategies pass Profisee data to Web-based data service providers and receive enriched data from the providers, based on the submitted data. The strategy specifies how to contact the Profisee server and the service provider, and controls where incoming data is written. Filters can be used with data service strategies to limit the number of calls made to service providers, as each call can result in a fee.

Service providers include such Web-based data providers as Dun & Bradstreet and Google.

### Notification Event

The *notification event* is an entry written to a Profisee table by the event publishing server when it locates an event in the transaction table that matches a condition in a scenario. The notification event is read by the event consuming server, which then passes it to the subscriber.The notification event alerts the subscriber that it should perform the work defined in the configuration.

This event does not contain the information from the triggering event. Instead, it indicates that a match for a particular scenario has occurred. For example, if a subscriber is the Data Transfer Controller, the notification event could instruct the subscriber to transfer data to another Profisee server, based on the data transfer strategy in the configuration linked to the scenario.

Manually triggering events from the entity grid using Trigger Profisee Events bypasses the transaction table to produce a notification event.

The event publishing server monitors the transaction table for any events that match conditions defined in event scenarios. Events which match scenarios are called *triggering events*. When an event publishing server finds a triggering event, it then sends a notification event to the event consuming server.