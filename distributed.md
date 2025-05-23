# Distributed Systems

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
