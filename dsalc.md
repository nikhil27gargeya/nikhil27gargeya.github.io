# DSA

Most data structures are used in these basic ways:
1. Read
2. Search
3. Insert
4. Delete
5. Update

We often want to optimize for the steps taken as we want high performance algorithms with the data structures we choose (A Common Sense Guide to Data Structures, Wengrow)

Abstract Data Type: an ADT is a set of operations and behaviors, without specifying how its built internally (ie. containers: lists, sets, stacks, queues, dictionaries, priority queue)

Data structures can be neatly classified into contiguous or linked structures. Contiguous structures use single slabs of memory and include arrays, matrices, heaps, hash tables. Linked structures are composed of distinct chunks of memory bound together by pointers and include lists, trees, and graph adjacency lists.

Array: an ordered container represented by a contiguous block of memory that stores a fixed size, indexed collection of homogenous/same type of data. Same type of data relates to the contiguous nature because every cell must be the same size. Like street of houses, where each house has an address and the exact location can be determined by address.
python: arr = []
c++: int arr[]
runtimes:
Access element: O(1) because computer can identify the memory location with simple operation (address = base + (i * size_of_element)) and this is independent of array size hence O(1)
Searching: O(n) because in the worst case it needs to traverse the entire array
Insert: O(n) if shifting required; O(1) amortized when inserting at the end of a dynamic array
Remove: O(n) if shifting is required; O(1) when removing from the end
Updating: O(1) if index is known, O(n) if element must first be searched for 

Advantages
1. Constant time access given the index (each index maps to particular memory address, so with index, we can get data)
2. Space efficiency (no space wasted with metadata (data about data) / pointers / end of record information)
3. Memory locality (physical continuity that comes iwth contiguous structures exploits high speed cache memory on modern computer architectures)

Downsides:
1. Cannot be resized (hence why we have dynamic arrays)
For dynamic arrays, the doubling of size process involves allocating a new array of size 2n, copying the contents of the old array to the new one, and returning the space of the old array to the allocation system. The average number of moves per element is 2; hence, the total work of resizing is O(n). A dynamic array is asymptotically as efficient as allocating a perfectly sized array from the start. Insertions at the end, however, are no longer guaranteed O(1); they are O(1) amortized (average in the long term).
2. Expensive insertions / deletions, requires shifting elements
3. Single data type which is less flexible

So conceptually, an array is a container that stores values in a specific order, it is contiguously allocated and can be indexed to find an address in O(1). It has issues with insertions / deletions which requires shifting.

Linked List: non continguous block of memory that stores a node containing a value and pointer to the next node. Nodes not necessarily have to have the same type of value.
When implementing a linked list, sometimes there are sentinel nodes, which are dummy nodes added to both ends of the linked list and which head and tail always point to. Basically an empty list still contains the sentinels (head -> tail). Using sentinel nodes eliminates many edge cases when implementing linked list operations.
ie. insertAtBeginning


runtimes:
SLL (Singly Linked List) is where each node only has pointer to the successor element.
Access element: O(n) because computer cannot identify the memory location like it can with arrays
Search: O(n) because, in the worst case, it must traverse the entire linked list
Insert: O(1) at the beginning or after a known node; O(1) at the end if a tail pointer is maintained; O(n) if the insertion location must first be found
Remove: O(1) from the beginning or after a known previous node; O(n) from the end because the node before the tail must be found; O(n) if the removal location must first be found
Updating: O(1) if the node is already known; O(n) if the node must first be searched for

DLL (Doubly Linked List) is where each node points to predecessor and successor element. It simplifies these operations (trading off memory from the extra pointers)
1. Deleting a node when you have a pointer to it (the advantage is that instead of traversing the list to access the predecessor node), we can delete it in O(1) instead of O(n)
   Practical example of this is LRU cache, because we maintain hashmap of keys (which is whatever identifies the  cached item). For web cache, key is URL string, for db cache key is query string, for api server key is api request. The key basically is our input in the context of what our cache is designed for. Also the DLL neeeds to store the hashmap key of each node because during eviction, the DLL tells us which node to evict (the tail node), but to keep the hashmap in sync.
   What both data structures represent:
   1) hashmap: do I have this key cached? If so, how recently used is it?
   2) DLL: recency timeline, which was used least recently
2. Inserting before a given node
   4 point updates needed because prev/next for inserted node and next for the preceeding node and prev for the following node
3. Traversing backwards through the linked list
Also, an ordered hashmap works under the hood by combining with a DLL or array to track sequence of data (drawback is more space / memory usage)

Hashmap: unordered collection of key value pairs. Known as dictionary in python or swift.
Hashtable: similar to hashmap in the sense that it is an unordered collection of key value pairs but different than hashmap because no null keys or null values and is thread safe
Hashset: unordered collection of unique elements (more specific version of a set)


Divide and Conquer:
Steps:
1. Breaking down a problem into subproblems which are smaller instances of the same type of problem
2. Recursively solving the subproblems
3. Combining the answers

The splitting into subproblems is done on the way down the recursion tree. Each recursive call keeps dividing the problem until a base case is reached. As the recursive calls return, the results are combined.

D&C algorithms tackle a problem of size n by recursively solving subproblems of size n/b and combining these answers in O(n^d) time
Master Theorem(asymptotic analysis for a recurrence relation of a D&C algorithm): T(n) = aT(n/b) + O(n^d)
a = branching factor
b = shrinking factor
d = work done at each level

Greedy:





Base Case 
Divide, Recurse, Combine
ie. MergeSort
Base Case: if 0 or 1 element, return
Divide:
Split array into two halves
Conquer:
Recursively sort both halves
Combine:
Merge the halves
Recurrence Relation: T(n) = aT(n/b) + f(n) 
In this case, a = 2 (2 subproblems), b = 2 (each subproblem is size n/2)


Big O (worst case complexity): 
From least to most:
O(1): constant time meaning that runtime is independent of the input size
O(log n): logarithmic time
O(n): linear time meaning that runtime is proportional to the input size
O(n log n): linearithmic time
O(n^2): quadratic time meaning that runtime grows proportionallyto the square of the input size
O(2^n): exponential time

Runtime Complexity:
how long does it take to run an algorithm as size of the input problem grows

Spacetime Complexity:
working memory required by an algorithm as size of the input problem grows




Pointers are the connections that bind linked structures together, and they represent the address of a location in memory. A cell phone number can be thought of as a pointer to its owner, as they move around. 
All linked structures share certain properties:
1. each node contains one or more data fields
2. each node contains pointer field(s) to other node(s), this means much much of the space is devoted to pointers over data
3. pointer to head of the structure so we know where to access it (ie. head, root)








Algorithms:
An algorithm is a procedure to accomplish a specific task (takes any of possible input instances and transforms it to the desired output). An algorithmic problem describes the complete set of instances it must work on and its output after running on one of its instances. (Skiena, The Algorithm Design Manual)

3 desirable properties of a good algorithm:
1. Correct
2. Efficient
3. Easy to implement

These goals may not be simultaneously achievable (hence why tradeoffs are required)


Correct algorithms have a proof of correctness, which explains why every instance of the problem is transformed to the expected output












# LC75
Sliding Window has two types of problems (and its typically not used when constraints indicate there are negative numbers, because it would be uncertain whether shifting helps)
1. Fixed Size (set window size)
2. Dynamic Size (two pointers that move in the same direction which shrinks and expands the window depending on the subset being looked at in the array)

Sliding Window is used when a question asks to find a contiguous subset that fulfills certain conditions
Moving window across each element in an array or string. Instead of rechecking all of the elements each time, you slide the window left to right and update the necessary parts. This saves time. O(n^2) -> O(n)  
```
def max_sum_subarray(arr, k):
		#step one: get sum of the first k elements (our first window)
		#step two: get sum of the first k elements (our first window)
	  #[1, 4, 3, 2, 5, 9]
	current_window = sum(arr[:k]) //first window the sum is 8
	sum = window_sum // max sum (stores max) = 8
	for i in range (k, len(arr)) 
		// i in range (3, 6) i -> 3, 4, 5
		window_sum += arr[i] - arr[i - k]
		//arr[3] = 2 arr[3 - 3] = arr[0] basically this line adds the next number and gets rid of the first number in the window   
		max_sum = max(max_sum, current_window)
	return max_sum
```

