# Hibernate

Hibernate ORM (or simply Hibernate) is an object–relational mapping tool for the Java programming language. It provides
a framework for mapping an object-oriented domain model to a relational database. Hibernate handles object–relational
impedance mismatch problems by replacing direct, persistent database accesses with high-level object handling functions.

## JPA vs Hibernate

As we have seen so far, JPA is a specification. It provides common prototype and functionality to ORM tools. By
implementing the same specification, all ORM tools (like Hibernate, TopLink, iBatis) follows the common standards. In
the future, if we want to switch our application from one ORM tool to another, we can do it easily.

| JPA                                                                                                                                                                   | Hibernate                                                                                                                                                                            |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Java Persistence API (JPA) defines the management of relational data in the Java applications.                                                                        | Hibernate is an Object-Relational Mapping (ORM) tool which is used to save the state of Java object into the database.                                                               |
| It is just a specification. Various ORM tools implement it for data persistence.                                                                                      | It is one of the most frequently used JPA implementation.                                                                                                                            |
| It is defined in javax.persistence package.                                                                                                                           | It is defined in org.hibernate package.                                                                                                                                              |
| The EntityManagerFactory interface is used to interact with the entity manager factory for the persistence unit. Thus, it provides an entity manager.                 | It uses SessionFactory interface to create Session instances.                                                                                                                        |
| It uses EntityManager interface to create, read, and delete operations for instances of mapped entity classes. This interface interacts with the persistence context. | It uses Session interface to create, read, and delete operations for instances of mapped entity classes. It behaves as a runtime interface between a Java application and Hibernate. |
| It uses Java Persistence Query Language (JPQL) as an object-oriented query language to perform database operations.                                                   | It uses Hibernate Query Language (HQL) as an object-oriented query language to perform database operations.                                                                          |

## fetch types

- Eager Loading is a design pattern in which data initialization occurs on the spot.
- Lazy Loading is a design pattern which is used to defer initialization of an object as long as it's possible.

## associations

Association mappings are one of the key features of JPA and Hibernate. They model the relationship between two database
tables as attributes in your domain model. That allows you to easily navigate the associations in your domain model and
JPQL or Criteria queries.

JPA and Hibernate support the same associations as you know from your relational database model. You can use:

- one-to-one associations,

```java
@OneToOne
@JoinColumn(name = "fk_shippingaddress")
private ShippingAddress shippingAddress;
```

```java
@OneToOne(mappedBy = "shippingAddress")
private Customer customer;
```

- many-to-one, one-to-many associations and

```java
@ManyToOne
private Order order;
```

```java
@ManyToOne
@JoinColumn(name = "fk_order")
private Order order;
```

```java
@OneToMany
private List<OrderItem> items=new ArrayList<OrderItem>();
```

```java
@OneToMany
@JoinColumn(name = "fk_order")
private List<OrderItem> items=new ArrayList<OrderItem>();
```

```java
@OneToMany(mappedBy = "order")
private List<OrderItem> items=new ArrayList<OrderItem>();
```

- many-to-many associations.

```java
@ManyToMany
@JoinTable(name = "store_product",
        joinColumns = {@JoinColumn(name = "fk_store")},
        inverseJoinColumns = {@JoinColumn(name = "fk_product")})
private Set<Product> products=new HashSet<Product>();
```

You can map each of them as a uni- or bidirectional association. That means you can either model them as an attribute on
only one of the associated entities or on both. That has no impact on your database mapping, but it defines in which
direction you can use the relationship in your domain model and JPQL or Criteria queries.

## sessions

A Session is used to get a physical connection with a database. The Session object is lightweight and designed to be
instantiated each time an interaction is needed with the database. Persistent objects are saved and retrieved through a
Session object.

The session objects should not be kept open for a long time because they are not usually thread safe and they should be
created and destroyed them as needed. The main function of the Session is to offer, create, read, and delete operations
for instances of mapped entity classes.

Instances may exist in one of the following three states at a given point in time:

- transient − A new instance of a persistent class, which is not associated with a Session and has no representation in
  the database and no identifier value is considered transient by Hibernate.
- persistent − You can make a transient instance persistent by associating it with a Session. A persistent instance has
  a representation in the database, an identifier value and is associated with a Session.
- detached − Once we close the Hibernate Session, the persistent instance will become a detached instance.

A Session instance is serializable if its persistent classes are serializable.

### Session Interface Methods

There are number of methods provided by the Session interface, few ot them:

- Transaction beginTransaction() - Begin a unit of work and return the associated Transaction object.
- void cancelQuery() - Cancel the execution of the current query.
- void clear() - Completely clear the session.
- Connection close() - End the session by releasing the JDBC connection and cleaning up.
- Criteria createCriteria(Class persistentClass) - Create a new Criteria instance, for the given entity class, or a
  superclass of an entity class.
- Criteria createCriteria(String entityName) - Create a new Criteria instance, for the given entity name.
- Serializable getIdentifier(Object object) - Return the identifier value of the given entity as associated with this
  session.
- Query createFilter(Object collection, String queryString) - Create a new instance of Query for the given collection
  and filter string.
- Query createQuery(String queryString) - Create a new instance of Query for the given HQL query string.
- SQLQuery createSQLQuery(String queryString) - Create a new instance of SQLQuery for the given SQL query string.
- void delete(Object object) - Remove a persistent instance from the datastore.
- void delete(String entityName, Object object) - Remove a persistent instance from the datastore.
- Session get(String entityName, Serializable id) - Return the persistent instance of the given named entity with the
  given identifier, or null if there is no such persistent instance.
- SessionFactory getSessionFactory() - Get the session factory which created this session.
- void refresh(Object object) - Re-read the state of the given instance from the underlying database.
- Transaction getTransaction() - Get the Transaction instance associated with this session.
- boolean isConnected() - Check if the session is currently connected.
- boolean isDirty() - Does this session contain any changes which must be synchronized with the database?
- boolean isOpen() - Check if the session is still open.
- Serializable save(Object object) - Persist the given transient instance, first assigning a generated identifier.
- void saveOrUpdate(Object object) - Either save(Object) or update(Object) the given instance.
- void update(Object object) - Update the persistent instance with the identifier of the given detached instance.
- void update(String entityName, Object object) - Update the persistent instance with the identifier of the given
  detached instance.

## caches

Caching is a mechanism to enhance the performance of a system. It is a buffer memory that lies between the application
and the database. Cache memory stores recently used data items in order to reduce the number of database hits as much as
possible.

### First-level Cache￼

The first-level cache is the Session cache and is a mandatory cache through which all requests must pass. The Session
object keeps an object under its own power before committing it to the database.

If you issue multiple updates to an object, Hibernate tries to delay doing the update as long as possible to reduce the
number of update SQL statements issued. If you close the session, all the objects being cached are lost and either
persisted or updated in the database.

### Second-level Cache

Second level cache is an optional cache and first-level cache will always be consulted before any attempt is made to
locate an object in the second-level cache. The second level cache can be configured on a per-class and per-collection
basis and mainly responsible for caching objects across sessions.

Any third-party cache can be used with Hibernate. An org.hibernate.cache.CacheProvider interface is provided, which must
be implemented to provide Hibernate with a handle to the cache implementation.

### Query-level Cache

Hibernate also implements a cache for query resultsets that integrates closely with the second-level cache.

This is an optional feature and requires two additional physical cache regions that hold the cached query results and
the timestamps when a table was last updated. This is only useful for queries that are run frequently with the same
parameters.

## problems in hibernate

Fetching too much data is probably the biggest problem you can have when you use an ORM tool because it makes it very
easy to load way more data than necessary. This problem does not replicate in dev/test scenarios if the amount of test
data is rather small, and once data starts to accumulate in production, the data access layer can get exponentially
slower.

There are many problems that may occur:

- lack of batch updates
- lack of statement caching
- too much locking
- too many database roundtrips
- exotic associations that generate inefficient SQL statements
