# Service-oriented Architecture

The Learners Guild software is comprised of a suite of [micro-services][microservices-wikipedia] that work in unison to deliver all of the functionality needed by the overall system. This style of architecture is known as a [service-orented architecture (SOA)][soa-wikipedia]. SOA makes it easier for software components on computers connected over a network to cooperate. Every computer can run any number of services, and each service is built in a way that ensures that the service can exchange information with any other service in the network without human interaction and without the need to make changes to the underlying program itself.

SOA is fundamentally a network-powered extension of [modular programming][modular-programming-wikipedia] and the [Unix philosophy][unix-philosophy-wikipedia].

Services fall within one of three [service types](#service-types) and adhere to the specifications of their associated type.

## Why?

But ... isn't it easier to just build one big monolithic application? Maybe, but *probably not*. There are several advantages that you gain by thinking in terms of services rather than one big application, including:

### Ease of Ramp-up

When a new developer starts, rather than having to digest the entire system, she can start with a single service and begin to get her bearings. In fact, for a large application with many services, it may be the case that certain developers only touch a subset of the services in the overall system.

### Fewer Merge Conflicts and Continuous Deployment

Since all services communicate with each other via well-defined APIs, you can modify and redeploy one service without taking down the entire application. Furthermore, there's less contention among developers since codebases are smaller, with fewer dependencies.

### Avoids "NIH" Syndrome

Does an existing piece of software (open-source, SaaS, or otherwise) already provide the capabilities we need? Great. Let's use it! In the worst case, we may just have to write a small API "bridge" to provide the interface we want.

### Ease of Replacement

If a service needs to be replaced for some reason (scalability, maintainability, etc.), as long as we provide a consistent API to the consumers of that service, *how* something is implemented is irrelevant. This allows for drop-in replacement without disturbing the rest of the system.

### Best Tool for the Job

In a typical monolithic web application, there's typically a single data store (relational DBMS), front-end framework (server-rendered templates, React.js, or whatever), etc. Developers are then forced to figure out how to solve the problem within that framework. With an SOA approach, each service is responsible for its own data and interfaces.

## Service Types

The type of a service defines its purpose, appropriate scope for responsibilities, and how it interacts with other services.

If our SOA were a rainforest, the service types would be Trees, Animals, and Soil.

### Core

Core services manage internal data and business logic. They are networked and expose a secure web API.

**Examples**

- Identity Management (IDM)
- Feedback

### Interface

Interface services provide a UI and front-end behavior (validations, basic UX) for interacting with one or more core services. They range from command-line tools to full web or mobile apps.

**Examples**

- Command-Line Task List
- Locus

### Adapter

Adapter services provide a bridge between internal core services or between core services and third-party software. They are purpose-built to link data between two APIs and create a dependency buffer between them, thus insulating services against external changes.

**Examples**

- Slack Integration for Pairing Service
- Data Sync between Survey Software and Core Metrics Service
- Web Hook on GitHub to Capture Student Submissions and Update Challenge Service



<!-- references -->

[soa-wikipedia]:https://en.wikipedia.org/wiki/Service-oriented_architecture
[modular-programming-wikipedia]:https://en.wikipedia.org/wiki/Modular_programming
[unix-philosophy-wikipedia]:https://en.wikipedia.org/wiki/Unix_philosophy
[microservices-wikipedia]:https://en.wikipedia.org/wiki/Microservices
