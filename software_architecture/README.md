# Software architecture (microservices, SOA)

## What is service-oriented architecture (SOA)?

Service-oriented architecture (SOA) is an enterprise-wide approach to software development of application components
that takes advantage of reusable software components, or services. In SOA software architecture, each service is
comprised of the code and data integrations required to execute a specific business function — for example, checking a
customer’s credit, signing into a website or processing a mortgage application.

The service interfaces provide loose coupling, which means that they can be called with little or no knowledge of how
the integration is implemented underneath. Because of this loose coupling and the way the services are published,
development teams can save time by reusing components in other applications across the enterprise. This is both a
benefit and a risk. As a result of the shared access to the enterprise service bus (ESB), if issues arise, it can also
affect the other connected services.

XML data is a key ingredient for solutions that are based on SOA architecture. XML-based SOA applications can be used to
build web services, for example.

SOA emerged in the late 1990s and represents an important stage in the evolution of application development and
integration. Before SOA was an option, connecting a monolithic application to data or functionality in another system
required complex point-to-point integration that developers had to recreate for each new development project. Exposing
those functions through SOA eliminates the need to recreate the deep integration every time.

SOA provides four different service types:

- Functional services (i.e., business services), which are critical for business applications.
- Enterprise services, which serve to implement functionality.
- Application services, which are used to develop and deploy apps.
- Infrastructure services, which are instrumental for backend processes like security and authentication.

Each service consists of three components:

- The interface, which defines how a service provider will execute requests from a service consumer.
- The contract, which defines how the service provider and service consumer should interact.
- The implementation, which is the service code.

SOA services can be combined to create higher-level services and applications.

## What are microservices?

Like SOA, microservices architectures are made up of loosely coupled, reusable, and specialized components that often
work independently of one another. Microservices also use a high degree of cohesion, otherwise known as bounded context.
Bounded context refers to the relationship between a component and its data as a standalone entity or unit with very few
dependencies. Rather than being adopted enterprise-wide, microservices typically communicate via application programming
interfaces (APIs) to build individual applications that perform a specific business functionality (or functionality for
specific areas of the business) in a way that makes them more agile, scalable and resilient. Typically, Java is the
programming language of choice to develop Microservices. Other programming languages may also be used, such as Golang
and Python.

Microservices are a true cloud-native architectural approach, often operating in containers, which make them more
scalable and portable for the creation of independent services. Teams can use microservices to update code more easily,
use different stacks for different components and scale the components independently of one another, reducing the waste
and cost associated with having to scale entire applications because a single feature might be facing too much load.
Because of their independence, microservices produce services that are more fault-tolerant than the alternatives.
