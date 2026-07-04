# Backend

Topics: 
client-server architecture, HTTP request-response lifecycle, HTTP methods, headers, status codes, cookies, sessions, API design, REST APIs, GraphQL, gRPC, WebSockets, polling, long polling, authentication, authorization, OAuth 2.0, OpenID Connect, JWT, server-side frameworks, middleware, request validation, serialization, deserialization, file uploads, object storage, background jobs, worker processes, scheduled jobs, message queues, event-driven backends, caching, rate limiting, pagination, idempotency, dependency injection, backend architecture patterns, monoliths, modular monoliths, microservices, logging, metrics, tracing, API testing, integration testing, backend security, performance optimization

Springboot is a tool that makes developing web applications with Java Spring Framework faster.

Good for modular applications that are ideal for microservices.

Autoconfiguration intializes applications with pre-set dependencies

Redis(short for remote dictionary server): stores data in memory instead of on drive, in key/value pairs for low latency retrieval. God to use as a cache for web apps.

Kafka is a distributed data store for ingesting and processing streaming data in real-time. Good for building real-time streaming data pipelines. Used as a message broker or for taking in activity data.

API design:

JSON can have 3 categories:
1. Scalars (single atomic data points like Strings, numbers, booleans, null)
2. Arrays (ordered list of values)
3. Objects (unordered collections of key value pairs)

An endpoint is a location/point of entry to an API typically denoted by a URL where an API accepts requests to access data or perform an operation

Resources and collections:
A resource represents a specific piece of data or object that can be accessed via a unique URI. In an API that handles invoices and payments, each invoice would be a resource, with each resource having its own URI. For example, /invoices/645E79D9E14 is the **endpoint**  that uniquely idenitfies a single resource, in this case, the invoice with the ID 645E79D9E14. (https://apisyouwonthate.com/blog/understanding-resources-and-collections-in-restful-apis/)




A collection is a group of resources, and a list or set of all the items of a particular type.
