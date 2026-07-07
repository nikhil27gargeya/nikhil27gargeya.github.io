# Backend

Topics: 
client-server architecture, HTTP request-response lifecycle, HTTP methods, headers, status codes, cookies, sessions, API design, REST APIs, GraphQL, gRPC, WebSockets, polling, long polling, authentication, authorization, OAuth 2.0, OpenID Connect, JWT, server-side frameworks, middleware, request validation, serialization, deserialization, file uploads, object storage, background jobs, worker processes, scheduled jobs, message queues, event-driven backends, caching, rate limiting, pagination, idempotency, dependency injection, backend architecture patterns, monoliths, modular monoliths, microservices, logging, metrics, tracing, API testing, integration testing, backend security, performance optimization

Client server architecture:
A computing model where multiple clients (users or devices) communicate with a server to access data, resources, or services. The client triggers requests (commonly in form of HTTP messages but could be other protocols) to a server's IP address. The server listens on a specific port and handles the incoming requests. It runs logic, queries a db if needed, then prepares a response. Once this processing is done, the server sends the result back. The client receives the response and renders it on screen. 
Client server architecture can be 1 tier/monolithic, 2 tier, 3 tier (includes dedicated application layer), n-tier (dedicated layers for caching, authentication, analytics, API gateways, etc.)

HTTP request-response lifecycle:
HTTP is a communication protocol that defines how clients and servers communicate. HTTP protocol is stateless (each request is independent and server has no memory of previous requests by default). HTTPS encrypts the communicated data using TLS, more on encryption later) which defines:
1. where request is sent (the URL identifies the server and requested resource, such as https://yourservice.com/api/auth/signup)
2. request method (GET, POST, PUT, DELETE)
3. headers (metadata about the request and/or the response)
4. status codes (indicates result of the request)
5. Request and response body (JSON is commonly found in the HTTP body, but HTTP does not require it)

URL vs URI vs URN:
URI (Uniform Resource Identifier): string that identifies a resource (represenation of a specific piece of data or object). It may identify the resource by location, by name, or through another URI scheme. (ie. mailto:alice@example.com)
URL (Uniform Resource Locator): string that denotes the location of a given resource (ie. https://example.com/users/42)
URN (Uniform Resource Name): identifies a resource by name rather than by location (ie. urn:isbn:9780140328721)

API design:
An API is set of definitions and protocols that enables software components to communicate

Why have APIs:
To enable developers to avoid rebuilding application features that already exist (https://www.cloudflare.com/learning/security/api/what-is-api-endpoint/)

An endpoint is a location (point of entry to an API) typically identified by a URL, where an API accepts requests to access data or perform an operation.

Resources and collections:
A resource is a specific piece of data or object that can be accessed via a unique URI. In an API that handles invoices and payments, each invoice would be a resource, with each resource having its own URI. For example, /invoices/645E79D9E14 is the resource path that uniquely idenitfies a single resource, in this case, the invoice with the ID 645E79D9E14. (https://apisyouwonthate.com/blog/understanding-resources-and-collections-in-restful-apis/). GET /invoices/645E79D9E14 would be the endpoint.

What is a RESTful API:
An API that conforms to the REST (representational state transfer) architecture style (it is not a protocol, but rather a set of constraints). At its core, it revolves around the idea of resources, which can be any piece of information like a user, product, document, or collection of items. (https://cloud.google.com/discover/what-is-rest-api). When a client request is made via a REST API, it transfers a reprentation of the state of the resource to the endpoint. This information is delivered in one of several formats via HTTP (JSON, HTML, XML, Python, PHP, plain text). JSON is popular because it is language agnostic and readable by humans and machines (https://www.redhat.com/en/topics/api/what-is-a-rest-api). 

In order for an API to be considered RESTful, it must have:
A client-server architecture made up of clients, servers, and resources, with requests managed through HTTP.
Stateless client-server communication, meaning no client information is stored between get requests and each request is separate and unconnected.
Cacheable data so clients can avoid making unnecessary requests
Uniform interface between components so data is transferred in standard way (resources are identified by URIs, actions are performed through standard HTTP methods, and data is transferred as representations, such as JSON. The resource itself is separate from the representation sent to the client)
Layered system that organizes each type of server into hierarchies, invisible to the client
Code on demand (server can send exectuable code to the client)

When a client executes a call, it parses a URL:
URL:            https://myapp.com/v2/profiles
Scheme:         https
Domain/host:    myapp.com
Request target: /v2/profiles
Endpoint:       GET https://myapp.com/v2/profiles
HTTP request:   GET /v2/profiles HTTP/1.1
                Host: myapp.com
                Accept: application/json
                
                {blank line represents end of request headers}
                {Request body, such as JSON body would go here if needed}

HTTP Methods (correlates with CRUD operations):
GET (retrieves data from a server without modifying anything), typically does not include a request body. Although a request body is possible, it usually has no defined semantic meaning and may be ignored by the server.
POST (submits new data to a server to create a resource),
PUT (replaces a target resource with uploaded payload)
PATCH (partially updates target resource with uploaded payload, sends fields that need to change)
DELETE (removes specified resource from the server)

API Headers:
represents key-value metadata associated with an api request and response
Examples:
Content-Type: application/json (header that describes the body)
Authorization: Bearer abc123token (request authorization)
Cache-Control: max-age=3600 (telling client whether it can reuse a response)
Set-Cookie: sessionId=abc123 (store cookie and send back on future requests)

Status Codes:
1xx (Informational, these responses are provisional and do not represent a final outcome)
2xx (Success)
- 200 means request successful (request was received, understood, processed, and requested content was returned normally)
- 201 means request successful and resource created
- 202 means accepted (request has been received and accepted, but is still being processed, typically seen in asynchronous operations where immediate completion is not possible)
- 204 means no content (server successfully processed request but does not need to return a response body)
3xx (Redirection, instruct the client to take additional action to complete the request, usually by requesting a different URL)
- 301 means moved permanently (URL has moved permanently, does not guarantee the same HTTP method or request body is preserved)
- 302 means found (URL is temporarily moved)
- 304 means not modified (requested resource has not changed since the last time it was retrieved)
- 308 means permanent redirect (similar to 301, permanent change on URL, but the difference is that it guarantees the same HTTP method and request body is preserved
Preservation: when a redirected request keeps the same HTTP method and request body as the original request
4xx (Client error)
- 400 means bad request (server cannot process due to syntax issues, invalid parameters, or unreadable/corrupted data sent by client)
- 401 means unauthorized (server does not receive valid authorization credentials)
- 403 means forbidden (server does not grant access to resource)
- 404 means not found (requested resource is not available and may or may not come back)
- 406 means not acceptable (server cannot generate a response that matches acceptable values defined in request's headers)
- 407 means proxy authentication required (client must authenticate with proxy server before request can be fulfilled)
- 408 means request timeout (server did not receive complete request in expected time frame, and closed the connection)
- 409 means conflict (request could not be completed due to conflict with the current state of the resource)
- 429 means too many requests (client has sent too many requests in a given timeframe. Prevents excessive traffic)
5xx (Server error)
- 500 means internal server error (generic code when server cannot fulfill the request)
- 501 means not implemented (request method or feature is not recognized or has not been enabled on the server)
- 502 means bad gateway (when server acting as a gateway receives invalid response from upstream server)
- 504 means gateway timeout (similar to 502, but instead of invalid response, there is no response received within given timeframe)


Cookies vs Sessions vs Tokens:

Cookies:
Cookies are small pieces of data that a server sends to a client to enable features like session management, personalization, and user tracking. Server response contains Set-Cookie header (ie. Set-Cookie: userId=xyz12345) and client stores that cookie. On subsequent requests, the client includes the cookie header with the stored value. In a stateful session, the cookie stores a random session ID. In a stateless cookie/token, the cookie itself contains encoded user/session information plus a cryptographic signature, allowing the backend to verify that the data was created by the server and not tampered with.

Sessions:


Tokens:






JSON can have 3 categories:
1. Scalars (single atomic data points like Strings, numbers, booleans, null)
2. Arrays (ordered list of values)
3. Objects (unordered collections of key value pairs)

A collection is a group of resources, and a list or set of all the items of a particular type.
Springboot is a tool that makes developing web applications with Java Spring Framework faster.

Good for modular applications that are ideal for microservices.

Autoconfiguration intializes applications with pre-set dependencies

Redis(short for remote dictionary server): stores data in memory instead of on drive, in key/value pairs for low latency retrieval. God to use as a cache for web apps.

Kafka is a distributed data store for ingesting and processing streaming data in real-time. Good for building real-time streaming data pipelines. Used as a message broker or for taking in activity data.


