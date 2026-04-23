# Event Processing Overview

## What is Event Processing?

Real-time event processing is the Profisee feature area that allows administrators to configure event triggers, either from Profisee or from an external system. These detected triggers then result in data changes through subscriptions, also configured by the Profisee administrator. Subscriptions can include transferring data between Profisee and an external system, querying service providers for information, starting workflows, or performing other work in custom-designed solutions. Event processing always involves a Profisee server at the hub.

## Application Data Transfers

Event processing is most frequently used with a data transfer subscription, which makes integration between Profisee and other systems possible. When a triggering event is detected, Profisee notifies the subscriber software, linked to the subscription configuration, to implement the data transfer actions configured in the subscription. Data transfers can occur between two Profisee systems, or between Profisee and an external system. Because notifications and triggering events are separate, the data transfer does not include any attributes or data changes included in the trigger. Multiple external systems are currently supported through specialized connector software that works in tandem with the data transfer subscriber. The connector is included as a part of the subscription.

## Data Service Calls

Data service subscriptions can also be used in event processing. Unlike data transfer subscriptions, data service subscriptions do not synchronize data between systems. Instead, Profisee data is sent to a Web-based data service provider, which returns enriched data based on the submitted information. The data service subscription can be triggered in the same way as the data transfer subscription, and like data transfers, data service calls rely upon connector software. Data service providers include Melissa Data and Dun & Bradstreet.

## Queue-based Systems

Event processing can also take the form of queue-based transactions, or workflows initiated by data changes. This process is handled by the MSMQ subscriber. Event processing through MSMQ is a legacy feature that has been replaced by the Data Transfer Controller and connectors.

### Academy Preview

The following content is from the Profisee Academy course on Event Processing. Academy customers can see the full course [here](https://support.profisee.com/lms/courseinfo?id=00u00000000002800aM).