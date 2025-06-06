# Fundamentals:

Language: tool to write code
Library: prewritten codebase that is a piece in the build
Framework: Blueprint on which your code functions on

Software exists within a framework
Software contains libraries

Code calls a library vs. Framework calls code

Strongly vs Weakly Typed:
Strongly Typed: type rules are enforced by the compiler. Error will be thrown if there are operations between incompatible types. Explicit conversions are required in most cases. (ie. python, java, c(has some implicit conversion, like int -> long bc no loss in precision), swift(has no implicit conversion))
Weakly Typed: type rules are not enforced by the compiler. Implicit/type conversions. (ie. javascript, php)

Statically vs Dynamically Typed:
Statically Typed: type rules are enforced at compile time, the compiler type checks at runtime (ie. java, c, swift)
Dynamically Typed: type rules are enforced at run time (ie. javascript, python)

Pros of Swift:
Type Inference
Strongly typing (type safe)
Optionals
ARC Memory management

Cons:
Documentation changes rapidly(ie. Migrating from the Observable Object protocol to the Observable macro)
Tied to Xcode

Shallow copy vs Deep copy:
Shallow copy: a new object with references to the original object's data, changes affect the original
Deep copy: a new object with independent copies, changes don't affect the original

Pointer vs Reference
Pointer: stores a memory address, it points to the location of data in memory
A pointer is a primitive data type just like an integer and character.

Primitive data type:
basic data types built into a language (ie. int, char, float, void), stored on the stack

Non-Primitive data type:
built from primitive types or built by programmer (arrays, linked lists, stacks, queues, etc.) and these objects stored on the heap (their reference variables still exist on the stack)

Size of data types:
Integer: 4 bytes
Character: 1 byte
Pointer: 4 bytes on 32 bit machine, 8 bytes on 64 bit machine

Reference: an alias variable 

One difference between a pointer and a reference is that a pointer can be reassigned

Shared Pointer:
pointer that retains shared ownership of an object through a reference count, used for memory management

STL (standard template library):
template classes that provide the common data structures and algorithms like lists, stacks, arrays, sorting, searching
the four components are containers, algorithms, iterators, functors
Containers are data structures and include sequence containers (arrays which are non-resizable, vectors which are resizable, deque, list with is doubly linked list, forward list which is singly linked list), container adaptors (stack LIFO, queue FIFO, priority queue which uses vector as underlying structure), associative containers (sets which is ordered, maps which are sorted by keys using Compare function, multisets, multimaps), unordered associated containers (unordered set, unordered multiset, unordered map, unordered multimap)

Vector:
push_back vs emplace_back
push_back is for constructs and appends a copy of that element
emplace_back is to construct and append an element in place within the container
reserve(): reserves memory for at least a specificied number of elements

Function Signature:
function name + parameters

--version command can tell you what version you are using


Networking:
TCP: Transmission Control Protocol
3 way handshake: SYN (synchronize), SYN-ACK (synchronize acknowledge), ACK (acknowledge)
Seq Number: counter used to track every byte sent outward by a host (doesn't start at 1 for security reasons)


Web Socket:
Context: Chatting Application
Person 1 and Person 2 both have instances of their application
Server and Database that stores conversation data
In a REST model, Person 1 application sends POST request (containing room, user id, message payload) to the server and database will store it
When Person 2 responds, this response is retrieved with a GET request from Person 1's application 
Issue here is that we don't know how to notify Person 2 to pull the request. This can be solved using short polling, meaning that when the application loads up, it will send a GET request asking for any new messages. However, this is not efficient at all, because of latency delay between api calls. Long polling would be keeping the request open until the database changes, but this utilizes server resources constantly which is inefficent (ie. memory, threads).
In the Web Socket model, Person 1 and Person 2 application establishes connection to the server (indicating that the user is present). When a message is sent, the server will broadcast the message out to the recipient user. So, instead of request-response which is client-initiated, server can initiate and push content which is bidirectional.
