# Spring

The Spring Framework is an application framework and inversion of control container for the Java platform. The
framework's core features can be used by any Java application, but there are extensions for building web applications on
top of the Java EE (Enterprise Edition) platform. Although the framework does not impose any specific programming model,
it has become popular in the Java community as an addition to the Enterprise JavaBeans (EJB) model. The Spring Framework
is open source.

## Features

- Core technologies: dependency injection, events, resources, i18n, validation, data binding, type conversion, SpEL,
  AOP.
- Testing: mock objects, TestContext framework, Spring MVC Test, WebTestClient.
- Data Access: transactions, DAO support, JDBC, ORM, Marshalling XML.
- Spring MVC and Spring WebFlux web frameworks.
- Integration: remoting, JMS, JCA, JMX, email, tasks, scheduling, cache.
- Languages: Kotlin, Groovy, dynamic languages.

## Spring core

### What is inversion of control (IoC) and dependency injection (DI)?

In software engineering, inversion of control (IoC) is a programming technique in which object coupling is bound at run
time by an assembler object and is typically not known at compile time using static analysis.
In traditional programming, the business logic flow is determined by objects that are statically assigned to one
another.
With inversion of control, the application flow depends on the object graph instantiated by the assembler and is made
possible by object interactions defined through abstractions. The binding process is achieved through “dependency
injection“.
Inversion of control is a design paradigm to give more control to the targeted components of the application, the ones
that are actually doing the work.
Dependency injection is a pattern used to create instances of objects that other objects rely on upon without knowing at
compile time which class will be used to provide that functionality.
Inversion of control relies on dependency injection because a mechanism is needed to activate the components providing
the specific functionality. Otherwise, how will the framework know which components to create if it is no longer in
control?
In Spring, dependency injection may happen in the following ways:

- Constructor injection
- Setter injection
- Fields Injection

### Explain inversion of control in spring framework?

In spring framework, inversion of control refers to the framework’s ability to create, destroy, and manage the beans’
lifecycle.
The ApplicationContext (internally, it uses BeanFactory) is in the center of inversion of control in Spring.
To assemble beans, the spring bean factory uses configuration metadata, which can be in the form of XML configuration or
annotations.

### Difference between BeanFactory and ApplicationContext?

A BeanFactory is like a factory class that contains a collection of beans. The BeanFactory holds bean definitions within
itself and then instantiates a bean whenever asked for by clients.
BeanFactory is able to create associations between collaborating beans as they are instantiated. BeanFactory also takes
part in the life cycle of the beans, making calls to custom initialization and destruction methods.
At a high level, an application context is the same as a bean factory. Both load bean definitions, wire beans together,
and dispense beans upon request. But the application context also provides:

- A means for resolving text messages, including support for internationalization.
- A generic way to load file resources.
- Events to beans that are registered as listeners.
  The three commonly used implementations of ApplicationContext are:
- ClassPathXmlApplicationContext: loads context definition from an XML file located in the classpath, treating context
  definitions as classpath resources. The application context is loaded from the application’s classpath by using the
  code.ApplicationContext context = new ClassPathXmlApplicationContext(“bean.xml”);
- FileSystemXmlApplicationContext: loads context definition from an XML file in the filesystem. The application context
  is loaded from the file system by using the code. ApplicationContext context = new FileSystemXmlApplicationContext(
  “bean.xml”);
- XmlWebApplicationContext: loads context definition from an XML file contained within a web application.

### In how many ways, we can configure spring into our applications?

we can configure Spring into our applications in 3 ways:

- XML based configuration
- Annotation-based configuration
- Java-based configuration

### What is XML configuration for spring?

In Spring framework, the required dependencies and the services are specified in external configuration files, which are
typically in an XML format. These XML configuration files usually start with <beans> tag and contain a lot of bean
definitions AND application-specific configuration options.
The main goal of Spring XML Configuration is to have all the Spring components configured by using XML files.
It means that there will not be present any other type of Spring Configuration (like annotations or configuration via
Java classes).
A Spring XML Configuration uses Spring namespaces to make available the sets of XML tags used in the configuration; the
main Spring namespaces are context, beans, JDBC, tx, aop, mvc, etc.

### What is Java-based configuration in spring?

The central artifacts in Spring’s java-configuration support are @Configuration annotated classes and @Bean annotated
methods.
The @Bean annotation is used to indicate that a method instantiates, configures and initializes a new object to be
managed by the Spring IoC container. @Bean annotation plays the same role as the <bean/> element.
Annotating a class with @Configuration indicates that its primary purpose is as a source of bean definitions.
Furthermore, @Configuration classes allow inter-bean dependencies to be defined by simply calling other @Bean methods in
the same class.

### What is spring annotation-based configuration?

Starting from Spring 2.5, it became possible to configure the dependency injection using annotations. So instead of
using XML to describe a bean wiring, we can move the bean configuration into the component class itself by using
annotations on the relevant class, method, or field declaration.
Annotation injection is performed before XML injection, thus the XML configuration will override the annotation
configuration when we wire the beans through both approaches.
Annotation wiring is not turned on in the Spring container by default. So, before we can use annotation-based wiring, we
must enable it in our Spring configuration file. So consider having the following configuration file if you want to use
any annotation in your Spring application.
Once <context:annotation-config/> is configured, you can start annotating your code to indicate that Spring should
automatically wire values into properties, methods, and constructors.
A few essential annotations which you will be using in this type of configuration are:

- @Required : The @Required annotation applies to bean property setter methods.
- @Autowired : The @Autowired annotation can apply to bean property setter methods, non-setter methods, constructor and
  properties.
- @Qualifier : The @Qualifier annotation along with @Autowired can be used to remove the confusion by specifiying which
  exact bean will be wired.
- JSR-250 Annotations : Spring supports JSR-250 based annotations which include @Resource, @PostConstruct and
  @PreDestroy annotations.

### Explain spring bean lifecycle?

The life cycle of a Spring bean is easy to understand. When a bean is instantiated, it may be required to perform some
initialization to get it into a usable state. Similarly, spring context may require some cleanup when the bean is no
longer needed and is removed from the container.

Spring bean factory is responsible for managing the life cycle of beans created through spring containers. The life
cycle of beans consist of call back methods which can be categorized broadly into two groups:

- Post initialization call back methods
- Pre destruction call back methods

Spring framework provides the following four ways for controlling life cycle events of bean:

- InitializingBean and DisposableBean callback interfaces
- Other Aware interfaces for specific behavior
- Custom init() and destroy() methods in bean configuration file
- @PostConstruct and @PreDestroy annotations

For example, customInit() and customDestroy() methods are examples of the life cycle methods.

### What are different spring bean scopes?

We can create the beans in the spring container in six bean scopes. All the scope names are self-explanatory, but let us
make them clear so there will be no doubt.

- Singleton (default): This bean scope is default and it enforces the container to have only one instance per spring
  container irrespective of how much time you request for its instance. This singleton behavior is maintained by bean
  factory itself.
- Prototype: This bean scope just reverses the behavior of singleton scope and produces a new instance each and every
  time a bean is requested.
- Request: With this bean scope, a new bean instance will be created for each web request made by client. As soon as
  request completes, bean will be out of scope and garbage collected.
- Session: Just like request scope, this ensures one instance of bean per user session. As soon as user ends its
  session, bean is out of scope.
- Application: global-session is something which is connected to Portlet applications. When your application works in
  Portlet container it is built of some amount of portlets. Each portlet has its own session, but if your want to store
  variables global for all portlets in your application than you should store them in global-session. This scope doesn’t
  have any special effect different from session scope in Servlet based applications.
- Websocket: enables two-way communication between a client and a remote host. Web socket provides a single TCP
  connection for traffic in both directions. This is specially useful for multi-user applications with simultaneous
  editing and multi-user games.

### What are inner beans in spring?

In Spring framework, whenever a bean is used for only one particular property, it’s advised to declare it as an inner
bean. And the inner bean is supported both in setter injection ‘property‘ and constructor injection ‘constructor-arg‘.

### Are singleton beans thread safe?

Spring framework does not do anything under the hood concerning the multi-threaded behavior of a singleton bean. It is
the developer’s responsibility to deal with the singleton bean’s concurrency issues and thread safety.

While practically, most spring beans have no mutable state (e.g., Service and DAO classes), and as such are trivially
thread-safe. But if your bean has a mutable state (e.g., View Model Objects), so you need to ensure thread safety.

The easiest and obvious solution for this problem is to change the scope of mutable beans from “singleton” to
“prototype“.

### Explain spring bean autowiring?

In the spring framework, setting bean dependencies in configuration files is a good practice, but the spring container
can also autowire relationships between collaborating beans.

This means that it is possible to automatically let Spring resolve collaborators (other beans) for your bean by
inspecting the contents of the BeanFactory.

Autowiring is specified per bean and can thus be enabled for some beans, while others will not be autowired.

### Explain different modes of bean autowiring?

There are five auto wiring modes in the spring framework. Let us discuss them one by one.

- no: This option is default for spring framework and it means that autowiring is OFF. You have to explicitly set the
  dependencies using tags in bean definitions.
- byName: This option enables the dependency injection based on bean names. When autowiring a property in bean, property
  name is used for searching a matching bean definition in configuration file. If such bean is found, it is injected in
  property. If no such bean is found, a error is raised.
- byType: This option enables the dependency injection based on bean types. When autowiring a property in bean,
  property’s class type is used for searching a matching bean definition in configuration file. If such bean is found,
  it is injected in property. If no such bean is found, a error is raised.
- constructor: Autowiring by constructor is similar to byType, but applies to constructor arguments. In autowire enabled
  bean, it will look for class type of constructor arguments, and then do a autowire by type on all constructor
  arguments. Please note that if there isn’t exactly one bean of the constructor argument type in the container, a fatal
  error is raised.
- autodetect: Autowiring by autodetect uses either of two modes i.e. constructor or byType modes. First it will try to
  look for valid constructor with arguments, If found the constructor mode is chosen. If there is no constructor defined
  in bean, or explicit default no-args constructor is present, the autowire byType mode is chosen.

### How do you turn on annotation based autowiring?

To enable @Autowired, you have to register AutowiredAnnotationBeanPostProcessor, and you can do it in two ways.

- Include <context:annotation-config > in bean configuration file.

```xml

<beans>
    <context:annotation-config/>
</beans>
```

- Include AutowiredAnnotationBeanPostProcessor directly in bean configuration file.

```xml

<beans>
    <bean class="org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor"/>
</beans>
```

### Explain @Autowired annotation with example?

The @Autowired annotation provides more fine-grained control over where and how autowiring should be accomplished. The
@Autowired annotation can be used to autowire bean on the setter method just like @Required annotation, constructor, a
property or methods with arbitrary names and/or multiple arguments.

For example, we can use @Autowired annotation on setter methods to get rid of the <property> element in the XML
configuration file. When Spring finds an @Autowired annotation used with setter methods, it tries to perform byType
autowiring on the method.

We can apply @Autowired to constructors as well. A constructor @Autowired annotation indicates that the constructor
should be autowired when creating the bean, even if no <constructor-arg> elements are used while configuring the bean in
the XML file.

### Explain @Qualifier annotation with example?

@Qualifier means, which bean is qualified to be autowired on a field. The qualifier annotation helps disambiguate bean
references when Spring would otherwise not be able to do so.

See below example, it will autowired a “person” bean into customer’s person property.

### Difference between constructor injection and setter injection?

Please find below the noticeable differences:

- In Setter Injection, partial injection of dependencies can possible, means if we have 3 dependencies like int, string,
  long, then its not necessary to inject all values if we use setter injection. If you will not inject then it will
  takes default values for those primitives.
- In constructor injection, partial injection of dependencies is not possible, because for calling constructor we must
  pass all the arguments right, if not so we may get error.
- Setter Injection will overrides the constructor injection value, provided if we write setter and constructor injection
  for the same property.
- But, constructor injection cannot overrides the setter injected values. It’s obvious because constructors are called
  to first to create the instance.
- Using setter injection you can not guarantee that certain dependency is injected or not, which means you may have an
  object with incomplete dependency.
- On other hand constructor Injection does not allow you to construct object, until your dependencies are ready.
- In constructor injection, if Object A and B are dependent each other i.e A is depends on B and vice-versa, Spring
  throws ObjectCurrentlyInCreationException while creating objects of A and B because A object cannot be created until B
  is created and vice-versa. So spring can resolve circular dependencies through setter-injection because Objects are
  constructed before setter methods invoked.

### What are the different types of events in spring?

Spring’s ApplicationContext provides the functionality to support events and listeners in code. We can create beans that
listen for events that are published through our ApplicationContext.

Event handling in the ApplicationContext is provided through the ApplicationEvent class and ApplicationListener
interface. So if a bean implements the ApplicationListener, then every time an ApplicationEvent gets published to the
ApplicationContext, that bean is notified.

Spring provides the following five standard events:

- ContextRefreshedEvent : This event is published when the ApplicationContext is either initialized or refreshed. This
  can also be raised using the refresh() method on the ConfigurableApplicationContext interface.
- ContextStartedEvent : This event is published when the ApplicationContext is started using the start() method on the
  ConfigurableApplicationContext interface. You can poll your database or you can re/start any stopped application after
  receiving this event.
- ContextStoppedEvent : This event is published when the ApplicationContext is stopped using the stop() method on the
  ConfigurableApplicationContext interface. You can do required house keeping work after receiving this event.
- ContextClosedEvent : This event is published when the ApplicationContext is closed using the close() method on the
  ConfigurableApplicationContext interface. A closed context reaches its end of life; it cannot be refreshed or
  restarted.
- RequestHandledEvent : This is a web-specific event telling all beans that an HTTP request has been serviced.

### Difference between FileSystemResource and ClassPathResource?

In FileSystemResource you need to give the path of spring-config.xml (Spring Configuration) file relative to your
project or the absolute location of the file.

In ClassPathResource spring looks for the file using ClassPath so spring-config.xml should be included in classpath. If
spring-config.xml is in “src” so we can give just its name because src is in the classpath path by default.

In one sentence, ClassPathResource looks in the classpath and FileSystemResource looks in the file system.

### Name some design patterns used in Spring Framework?

There are loads of different design patterns used, but there are a few obvious ones:

- Proxy – used heavily in AOP, and remoting.
- Singleton – beans defined in spring config files are singletons by default.
- Template method – used extensively to deal with boilerplate repeated code e.g. RestTemplate, JmsTemplate, JpaTemplate.
- Front controller – Spring provides DispatcherServlet to ensure an incoming request gets dispatched to your
  controllers.
- View Helper – Spring has a number of custom JSP tags, and velocity macros, to assist in separating code from
  presentation in views.
- Dependency injection – Center to the whole BeanFactory / ApplicationContext concepts.
- Factory pattern – BeanFactory for creating instance of an object.

## Spring Boot

Java Spring Boot (Spring Boot) is a tool that makes developing web application and microservices with Spring Framework
faster and easier through three core capabilities:

- Autoconfiguration
- An opinionated approach to configuration
- The ability to create standalone applications

These features work together to provide you with a tool that allows you to set up a Spring-based application with
minimal configuration and setup.

### Why is Spring Framework so popular?

Spring Framework offers a dependency injection feature that lets objects define their own dependencies that the Spring
container later injects into them. This enables developers to create modular applications consisting of loosely coupled
components that are ideal for microservices and distributed network applications.

Spring Framework also offers built-in support for typical tasks that an application needs to perform, such as data
binding, type conversion, validation, exception handling, resource and event management, internationalization, and more.
It integrates with various Java EE technologies such as RMI (Remote Method Invocation), AMQP (Advanced Message Queuing
Protocol), Java Web Services, and others. In sum, Spring Framework provides developers with all the tools and features
the need to create loosely coupled, cross-platform Java EE applications that run in any environment.

### What Spring Boot adds to Spring Framework

As capable and comprehensive as Spring Framework is, it still requires significant time and knowledge to configure, set
up, and deploy Spring applications. Spring Boot mitigates this effort with three important capabilities.

#### Autoconfiguration

Autoconfiguration means that applications are initialized with pre-set dependencies that you don't have to configure
manually. As Java Spring Boot comes with built-in autoconfiguration capabilities, it automatically configures both the
underlying Spring Framework and third-party packages based on your settings (and based on best practices, which helps
avoid errors). Even though you can override these defaults once the initialization is complete, Java Spring Boot's
autoconfiguration feature enables you to start developing your Spring-based applications fast and reduces the
possibility of human errors.

#### Opinionated approach

Spring Boot uses an opinionated approach to adding and configuring starter dependencies, based on the needs of your
project. Following its own judgment, Spring Boot chooses which packages to install and which default values to use,
rather than requiring you to make all those decisions yourself and set up everything manually.

You can define the needs of your project during the initialization process, during which you choose among multiple
starter dependencies—called Spring Starters—that cover typical use cases. You run Spring Boot Initializr by filling out
a simple web form, without any coding.

For example, the ‘Spring Web’ starter dependency allows you to build Spring-based web applications with minimal
configuration by adding all the necessary dependencies—such as the Apache Tomcat web server—to your project. ‘Spring
Security’ is another popular starter dependency that automatically adds authentication and access-control features to
your application.

#### Standalone applications

Spring Boot helps developers create applications that just run. Specifically, it lets you create standalone applications
that run on their own, without relying on an external web server, by embedding a web server such as Tomcat or Netty into
your app during the initialization process. As a result, you can launch your application on any platform by simply
hitting the Run command. (You can opt out of this feature to build applications without an embedded Web server.)

### Spring Boot vs. Spring Framework

Again, the biggest advantages of using Spring Boot versus Spring Framework alone are ease of use and faster development.
In theory, this comes at the expense of the greater flexibility you get from working directly with Spring Framework.

But, in practice, unless you need or want to implement a very unique configuration, using Spring Booth is worth the
tradeoff. You still are able to use Spring Framework’s very popular annotation system that lets you easily inject extra
dependencies (not covered by Spring Starters) into your application. And, you still get access to all Spring Framework
features, including easy event handling, validation, data binding, type conversion, and built-in security and testing
capabilities. Bottom line, if your project’s scope is covered by even just one Spring Starter, Spring Boot can
significantly streamline development.

### Why Spring Boot?

You can choose Spring Boot because of the features and benefits it offers as given here:

- It provides a flexible way to configure Java Beans, XML configurations, and Database Transactions.
- It provides a powerful batch processing and manages REST endpoints.
- In Spring Boot, everything is auto configured; no manual configurations are needed.
- It offers annotation-based spring application
- Eases dependency management
- It includes Embedded Servlet Container

### How does it work?

Spring Boot automatically configures your application based on the dependencies you have added to the project by using
@EnableAutoConfiguration annotation. For example, if MySQL database is on your classpath, but you have not configured
any database connection, then Spring Boot auto-configures an in-memory database.

The entry point of the spring boot application is the class contains @SpringBootApplication annotation and the main
method.

Spring Boot automatically scans all the components included in the project by using @ComponentScan annotation.

### Spring Boot Starters

Handling dependency management is a difficult task for big projects. Spring Boot resolves this problem by providing a
set of dependencies for developers convenience.

For example, if you want to use Spring and JPA for database access, it is sufficient if you include
spring-boot-starter-data-jpa dependency in your project.

Note that all Spring Boot starters follow the same naming pattern spring-boot-starter- *, where * indicates that it is a
type of the application.
