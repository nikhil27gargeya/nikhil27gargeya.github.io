# Computer Systems:

Topics: binary, hexadecimal, data representation, bits, bytes, words, integer representation, floating-point representation, Boolean logic, computer architecture, CPU structure, registers, instruction cycles, assembly language, machine code, memory hierarchy, CPU caches, cache locality, RAM, virtual memory, stack memory, heap memory, memory allocation, pointers, references, processes, threads, context switching, concurrency, parallelism, synchronization, locks, mutexes, semaphores, condition variables, deadlocks, operating systems, system calls, file systems, input/output, networking fundamentals, TCP/IP, UDP, DNS, sockets, compilers, interpreters, linking, loading

Number Systems:
The base tells us how many unique digits are used to represent numbers.

Decimal (Base 10):
Likely originated because humans counted on hands.
10 symbols:
0-9
529 = 5 × 10² + 2 × 10¹ + 9 × 10⁰ = 500 + 20 + 9 = 529

Binary (Base 2):
Used because  it is efficient for processing electronic signals.
On and off state represented by 0 and 1. 
1011 = 1 × 2³ + 0 × 2² + 1 × 2¹ + 1 × 2⁰ = 8 + 0 + 2 + 1 = 11 (decimal)

Hexadecimal (Base 16):
Used because its a compact way to represent binary numbers.
16 symbols:
0-9 (values 0 to 9)
A-F (values 10 to 15)
2F3 = 2 × 16² + F (15) × 16¹ + 3 × 16⁰ = 512 + 240 + 3 = 755 (decimal)

Converting between systems:
Decimal to binary:
Take the decimal number and keep dividing by 2, tracking the remainder until the quotient is 0. Then read the remainders from bottom to top.
13 = 1101
13 / 2 = 6 (R1)
6 / 2 = 3 (R0)
3 / 2 = 1 (R1)
1 / 2 = 0 (R1)

Binary to hexadecimal:
Group the binary digits in sets of four (starting from the right), then convert each group to its hexadecimal equivalent.
11011101 = DD
(1101) (1101)
1101 = D (13 in decimal)

Hexadecimal to decimal:
Multiply each digit by its place value in powers of 16, then add them up.
1A3 = 1 × 16² + A (10) × 16¹ + 3 × 16⁰ = 256 + 160 + 3 = 419 (decimal)




```
Bitwise Operators:
And (&)
Or (|)
Xor (^)
Not (~)
Left Shift (<<)
Right Shift (>>)

X Y   X & Y
0 0     0
0 1     0
1 0     0
1 1     1

X Y   X | Y
0 0     0
0 1     1
1 0     1
1 1     1

X Y   X ^ Y   (Exclusive or, can't have both)
0 0     0
0 1     1
1 0     1
1 1     0

5 << 1
0101 → 1010
= 10

5 >> 1
0101 → 0010
= 2
```

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

Pass by Value vs Pass by Reference:
Pass by value means copy of data is passed to the function so changes in the function don't affect the original variable
Pass by Reference means reference of the data is passed so changes in the function will affect the other



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

