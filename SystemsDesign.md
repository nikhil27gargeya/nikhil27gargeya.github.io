# Systems Design

Load Balancing (distributing workloads across servers):
https://www.cloudflare.com/learning/performance/what-is-load-balancing/
Its like having multiple checkout lines at a grocery store
Load balancer assigns each request to a server
Static load balancing algorithms do not take the current state of the system into account (in other words they are deterministic). Algorithms for this include round robin (rotational), weighted round robin, ip hashing. Risk is overburderning a server because we are giving it too many requests. 
Dynamic load balancing algorithms do take into account the current state of the system. Algorithms for this include least connection, least response time (request is sent to the server with the least response time). Dynamic load balancers must be aware of their server's health to route the requests accordingly.
usually sits between client and server instances

Real world example of load balancing:
AWS has ELB (elastic load balancer) that distributes traffic across EC2 instances, which improves availability
hardware load balancers (Citrix ADC, formerly NetScaler)

Consistent Hashing (distributing requests evenly across servers):
A node is a server/instance in the cluster. 
Depending on the system, that node could be a database, cache server, app server, or message broker.
Consistent hashing helps meditate problem where simple module hashing requires redistribution of data
it is a special kind of hashing used so that when a hash table is resized, only k/n keys need to be remapped (where k is the number of keys and n is the number of slots).
map servers onto a circular space (hash ring)
when new instance is added, we can redistribute only a portion of the events, everything else stays put
adding virtual nodes os that if some db fails, then the keys that it had are evenly distributed across other nodes
to address hot spots, we can use read replicas where we replicate popular keys across multiple nodes and load-balance reads across them

Real world example of consistent hashing:
cassandra (distributes data across ring), dynamodb (for partition placement)

Scaling:
vertical scaling: increasing CPU, memory, or storage to a single server. There is a cap on how much can be added..
horizontal scaling: adding more instances of servers to distribute the workload
Multi Tier Architecture (ie. where frontend interface, business logic, and db are separated)
Presentation Tier:
user interface, ui components, presentation logic
Application Tier (this tier processes requests, contains the business logic, and coordinates app's behavior)
application servers (software framework that processes business logic and manages data exchanges between clients and servers), APIs, business logic, middleware
Data Tier (responsible for storage, retrieval, and manipulation)
databases, data access layer (queries), data models

CAP theorem:
a distributed system can deliver only two of three desired characteristics: 
-consistency (all users/nodes see the same data and the same time)
-availability (every request gets a response, successful or not)
-partition tolerance (system works despite network failures between nodes)
(the ‘C,’ ‘A’ and ‘P’ in CAP).
This is important for the non-functional requirements, because we need to prioritize consistency or availability. Furthermore, if a network request fails between nodes, do we a) stop serving data (and prioritize consistency) or b) show wrong data (and prioritize availability)

Consistency achieved by:
-implements distributed transactions (hanges span across two or more independent networked nodes, ie. to cache and db)
-one node
-accepting higher latency
-postgresql, spanner, nosql w/ consistency (ie. dynamodb)

Availability achieved by:
-use multiple replicas
-eventual consistency is ok
-dbs with multiple availability zones, cassandra

Tinder example:
-availability for profile data (eventual consistency is fine)
-consistency for matching

Types of consistency (strongest to weakest):
Strong consistency: all reads reflect latest write
Causal consistency: related events appear in order (ie. no one should see comment to previous comment in incorrect order) 
Read your writes consistency: user sees their own updates
Eventual consistency: updates will propogate eventually


Caching:
A cache is a temporary storage that keeps recently used data handy so it can be retrieved faster the next time
accessing data from RAM is 10,000x faster than from disk (this gap is apparent when thousands of requests are being served per second)
External caching (like redis or memcached)
-runs on its own server and decoupled by the db
-when application needs data, it first checks the cache (cache hit or miss and fallback to db)




DNS protocol converts domain names to ip addresses


Most applications are data intensive. CPU power is rarely a limiting factor. 
Data Systems include:
Databases (stores data so that an application can find it later)
Cache (remembers result of an expensive operation, to speed up reads)
Search index (allows users to search data by keyword)
Stream Processing (send message to another process to be handled asynchronously)
Batch Processing (periodically crunch a large amount of data)

What is a read vs write:
When you read data, you are access information from a storage device (view), when you write, you are saving information onto a storage medium (modifying)

Combining serveral tools which is needed in a lot of cases requires use of an API which hides implementation from clients. 

What is a message queue:
asynchronous service-to-service communication (they store packets of data for other applications to use in the order they are transmitted)
It prevents loss of messages if there is a problem with the network or the application

Reliability (service works as intended and tolerates errors)
Scalability (as system grows, there are ways to deal with that growth)
Maintainability (sustaining current behavior and adapting system to new cases)

Fault vs Failure:
Fault: one component of spec deviating
Failure: system stops providing service to the user

Hardware Faults:
Hard disks have a mean time to failure of 10-50 years.
Adding redudancy helps this

Software Faults:
Bug
Runaway process

Human Errors:
This is why sandbox environments are useful
Unit test, whole system integration tests, manual tests

What is throughput:
the # of records that can be processed per second

Latency vs Response Time:
Latency: duration that a request is waiting to be handled, the awaiting service duration
Response Time: what client sees, basically service time + networking/queue delays

Response timw is better understood as a percentile of a distribution of values, rather than a single number, because a system that handles a variety of requests sees a difference in output
Testing scalability of a system requires sending requests independently of the response time, allowing for the queue to expand

Dichotomy (binary split) of vertical scaling (moving to more powerful machine) and horizontal scaling (distributed load across smaller machines) which is also known as shared-nothing architecture.

Elastic system is one that can automatically add comptuing resources when they detect a load increased, tradeoff is predictability and operational simplicity (manual is simpler operationally, but requires more predictability)

100,000 requests/sec × 1 KB/request = 100 MB/sec
3 requests/min × 2 GB/request = 6 GB/min = 100 MB/sec

Good Abstraction:
hides implementation detail behind a clean simple to understand facade

Agile (helps systems evolve):
test driven development and refactoring

Functional Requirements vs Nonfunctional requirements:
Functional Requirements: what it should do
Nonfunctional requirements: security, reliability, compliance, scalability
