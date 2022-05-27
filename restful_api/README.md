# RESTful APIs

REST is an acronym for REpresentational State Transfer and an architectural style for distributed hypermedia systems.
Like other architectural styles, REST has its guiding principles and constraints. These principles must be satisfied if
a service interface needs to be referred to as RESTful.

## rules and principles of RESTful API

The six guiding principles or constraints of the RESTful architecture are:

### Uniform Interface

By applying the principle of generality to the components interface, we can simplify the overall system architecture and
improve the visibility of interactions.

Multiple architectural constraints help in obtaining a uniform interface and guiding the behavior of components.

The following four constraints can achieve a uniform REST interface:

- Identification of resources – The interface must uniquely identify each resource involved in the interaction between
  the client and the server.
- Manipulation of resources through representations – The resources should have uniform representations in the server
  response. API consumers should use these representations to modify the resources state in the server.
- Self-descriptive messages – Each resource representation should carry enough information to describe how to process
  the message. It should also provide information of the additional actions that the client can perform on the resource.
- Hypermedia as the engine of application state – The client should have only the initial URI of the application. The
  client application should dynamically drive all other resources and interactions with the use of hyperlinks.

### Client-server

The client-server design pattern enforces the separation of concerns, which helps the client and the server components
evolve independently.

By separating the user interface concerns (client) from the data storage concerns (server), we improve the portability
of the user interface across multiple platforms and improve scalability by simplifying the server components.

While the client and the server evolve, we have to make sure that the interface/contract between the client and the
server does not break.

### Stateless

Statelessness mandates that each request from the client to the server must contain all of the information necessary to
understand and complete the request.

The server cannot take advantage of any previously stored context information on the server.

For this reason, the client application must entirely keep the session state.

### Cacheable

The cacheable constraint requires that a response should implicitly or explicitly label itself as cacheable or
non-cacheable.

If the response is cacheable, the client application gets the right to reuse the response data later for equivalent
requests and a specified period.

### Layered system

The layered system style allows an architecture to be composed of hierarchical layers by constraining component
behavior.

For example, in a layered system, each component cannot see beyond the immediate layer they are interacting with.

### Code on demand (optional)

REST also allows client functionality to extend by downloading and executing code in the form of applets or scripts.

The downloaded code simplifies clients by reducing the number of features required to be pre-implemented. Servers can
provide part of features delivered to the client in the form of code, and the client only needs to execute the code.

## http methods

### HTTP GET

Use GET requests to retrieve resource representation/information only – and not to modify it in any way. As GET requests
do not change the state of the resource, these are said to be safe methods.

Additionally, GET APIs should be idempotent, which means that making multiple identical requests must produce the same
result every time until another API (POST or PUT) has changed the state of the resource on the server.

If the Request-URI refers to a data-producing process, it is the produced data that shall be returned as the entity in
the response and not the source text of the process, unless that text happens to be the output of the process.

For any given HTTP GET API, if the resource is found on the server, then it must return HTTP response code 200 (OK) –
along with the response body, which is usually either XML or JSON content (due to their platform-independent nature).

In case the resource is NOT found on the server then it must return HTTP response code 404 (NOT FOUND).

Similarly, if it is determined that the GET request itself is not correctly formed then the server will return the HTTP
response code 400 (BAD REQUEST).

### HTTP POST

Use POST APIs to create new subordinate resources, e.g., a file is subordinate to a directory containing it or a row is
subordinate to a database table.

When talking strictly in terms of REST, POST methods are used to create a new resource into the collection of resources.

Ideally, if a resource has been created on the origin server, the response SHOULD be HTTP response code 201 (Created)
and contain an entity that describes the status of the request and refers to the new resource, and a Location header.

Many times, the action performed by the POST method might not result in a resource that can be identified by a URI. In
this case, either HTTP response code 200 (OK) or 204 (No Content) is the appropriate response status.

Responses to this method are not cacheable unless the response includes appropriate Cache-Control or Expires header
fields.

Please note that POST is neither safe nor idempotent, and invoking two identical POST requests will result in two
different resources containing the same information (except resource ids).

### HTTP PUT

Use PUT APIs primarily to update an existing resource (if the resource does not exist, then API may decide to create a
new resource or not).

If a new resource has been created by the PUT API, the origin server MUST inform the user agent via the HTTP response
code 201 (Created) response and if an existing resource is modified, either the 200 (OK) or 204 (No Content) response
codes SHOULD be sent to indicate successful completion of the request.

If the request passes through a cache and the Request-URI identifies one or more currently cached entities, those
entries SHOULD be treated as stale. Responses to PUT method are not cacheable.

The difference between the POST and PUT APIs can be observed in request URIs. POST requests are made on resource
collections, whereas PUT requests are made on a single resource.

### HTTP DELETE

As the name applies, DELETE APIs are used to delete resources (identified by the Request-URI).

A successful response of DELETE requests SHOULD be an HTTP response code 200 (OK) if the response includes an entity
describing the status, 202 (Accepted) if the action has been queued, or 204 (No Content) if the action has been
performed but the response does not include an entity.

DELETE operations are idempotent. If you DELETE a resource, it’s removed from the collection of resources.

Repeatedly calling DELETE API on that resource will not change the outcome – however, calling DELETE on a resource a
second time will return a 404 (NOT FOUND) since it was already removed.

Some may argue that it makes the DELETE method non-idempotent. It’s a matter of discussion and personal opinion.

If the request passes through a cache and the Request-URI identifies one or more currently cached entities, those
entries SHOULD be treated as stale. Responses to this method are not cacheable.

### HTTP PATCH

HTTP PATCH requests are to make a partial update on a resource. If you see PUT requests also modify a resource entity,
so to make more clear – the PATCH method is the correct choice for partially updating an existing resource, and PUT
should only be used if you’re replacing a resource in its entirety.

Please note that there are some challenges if you decide to use PATCH APIs in your application:

- Support for PATCH in browsers, servers, and web application frameworks is not universal. IE8, PHP, Tomcat, Django, and
  lots of other software has missing or broken support for it.
- Request payload of a PATCH request is not straightforward as it is for PUT request. e.g.

The PATCH method is not a replacement for the POST or PUT methods. It applies a delta (diff) rather than replacing the
entire resource.

## safe and idempotent methods

### Safe Methods

As per HTTP specification, the GET and HEAD methods should be used only for retrieval of resource representations – and
they do not update/delete the resource on the server. Both methods are said to be considered “safe“.

This allows user agents to represent other methods, such as POST, PUT and DELETE, in a unique way so that the user is
made aware of the fact that a possibly unsafe action is being requested – and they can update/delete the resource on the
server and so should be used carefully.

### Idempotent Methods

The term idempotent is used more comprehensively to describe an operation that will produce the same results if executed
once or multiple times.

Idempotence is a handy property in many situations, as it means that an operation can be repeated or retried as often as
necessary without causing unintended effects.

With non-idempotent operations, the algorithm may have to keep track of whether the operation was already performed or
not.

In HTTP specification, The methods GET, HEAD, PUT and DELETE are declared idempotent methods.

Other methods OPTIONS and TRACE SHOULD NOT have side effects, so both are also inherently idempotent.
