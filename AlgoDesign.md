# Algorithm Design

Algorithm: procedure that takes any of the possible input instances and transforms it to the desired output

An algorithmic problem is specified by describing the input space (complete set of instances) it must work on and the desired output for each instance. So, a problem is the general task, and the instance is a specific input of the problem.

3 desirable properties of a good algorithm
Correct, Efficient, Easy to implement

Correct algorithms need a proof of correctness.

Data Structures:
The whole point of data structures is to understand the inherent tradeoffs of data structure design. A given data representaiton may permit efficient implementation of certain operations at the cost that other operations are expensive.

What is an Abstract Data Type (ADT): They describe a set of well defined operations that act as a problem solving tool. However, they do not dictate how these operations must implemented, they are only concerned with the specifications of the operations (what they do and how they work).
Important classes include: containers, dictionaries, and priority queues

One dichotomy that exists in data structures is the idea of contiguous or linked memory. Contiguously allocated structures are composed of single slabs of memory and include arrays, matrices, heaps, and hash tables.
Linked data structures are composed of distinct chunks of memory which are bound together by pointers, and these include lists, trees, and graph adjacency lists.

Arrays:
they are like a street full of houses, where each array element is a house and the index is the house number.

Advantages:
Constant time access given the index
Space efficiency since the array purely data so no space is wasted with formatting information or end of record information
Offer great memory locality because the physical continuity between data accesses utilizes high speed cache memory 

Disadvantages:
Cannot adjust size, dynamic arrays solve this by utilizing a doubling strategy: when the array gets full, allocate array twice as big, copy all the elements into the new array, free the old array. Each element is copied log sub 2 (n) times.

[need to complete this]

What is amortized runtime:
average performance in the worst case

Pointers: connections that hold the pieces of linked structures together, and they represent the address of a location in memory. 
a var storing a pointer can provide more freedom than storing a copy of the item
a cell phone # is like a pointer to the owner

Stacks and Queues:
Container: a data structure that permits storage and retrieval of data items independent of content

Stacks: Retrieval is LIFO
Advantage:
simple to implement, best to use when retrieval order doesn't matter at all, like processing batch jobs
LIFO examples: subway, food in a refrigerator
Queue: Retrieval is FIFO
Dictionary: Access to data items by content

