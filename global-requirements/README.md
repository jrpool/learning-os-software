# Global Requirements

All of our software has certain requirements that must be considered "global" to the entire system. These requirements are not "functional" in nature; that is, they don't satisfy a particular end-user story. Instead, they are more akin to "constraints" placed on the development of the overall system.

### [Lean](lean.md)

### [Service-oriented Architecture](soa.md)

### Simple Interfaces First

Services are as heavy as they need to be, but never heavier. The human interface has a strong influence on service complexity; to keep the service simple, start by ensuring a simple interface.

Each human-facing service should expose a command line interface when possible, in addition to any GUI. Solve the simplest problem with the simplest solution. Keep it simple.

It may be the case that there are _multiple_ command-line interfaces. For example, a Group Collaboration Service might provide commands or "bot" interactions to allow interactions with various services.

An archetypal evolution of a service looks something this:

1. Born as an idea for system behavior
2. Captured as written guidelines
3. Practiced in human behavior and interactions
4. Need for software identified; third-party software adapted to use
5. Need for greater specialization; service designed and specs written
6. Text-based interface service built
7. New features push boundaries of text-based interface; GUI designed
8. GUI interface built for service

### No Tight Coupling to Third-Party Services

Wherever possible, in the case where one of the services in the system is maintained by a third-party, an adapter or bridge should be written which we *do maintain*.

As an example, let's imagine that we have settled on Slack as a group-communication platform. We should have an API bridge service that handles all incoming and outgoing web-hooks for Slack, such that if one of our services wants to "notify a user", it can simply invoke an API on our bridge service, which will be a thin-wrapper around a Slack API call to send a "direct message".

### Scale

In the long-term, there may be data associated with millions of unique users. All synchronous API calls should respond in under 300ms, regardless of the amount of data the system owns.

Furthermore, in the long-term, there may be as many as tens of thousands of users using the system simultaneously. All services should be designed with horizontal scalability in mind, such that, as response times increase, they can be driven back down by adding additional instances of the service.

### Responsive User Experience

Every service with a web-based user interface must be mobile-responsive. All interface designs must take into account the reality that, while commuting, users may want to at least browse and read information. The mobile interface does not need to support *every* interaction, just the ones that make sense on a mobile device.
