# DSA

Topics: abstract data types, time complexity, space complexity, Big-O, Big-Theta, Big-Omega, amortized analysis, arrays, dynamic arrays, strings, linked lists, stacks, queues, deques, hash tables, sets, maps, trees, binary trees, binary search trees, balanced trees, heaps, priority queues, tries, graphs, graph representations, sorting algorithms, searching algorithms, recursion, backtracking, two pointers, sliding window, prefix sums, binary search, divide and conquer, greedy algorithms, dynamic programming, breadth-first search, depth-first search, shortest-path algorithms, minimum spanning trees, union-find, topological sorting

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
When implementing a linked list, sometimes there are sentinel nodes, which are dummy nodes added to both ends of the linked list and which head and tail always point to. Basically an empty list still contains the sentinels (head sentinel -> tail sentinel). Without using sentinels, an empty list has no nodes, head and tail point to null. Using sentinel nodes eliminates many edge cases when implementing linked list operations.
ie. insertAtBeginning
without sentinel nodes, head may be null, so insertion requires a separate case for empty list.
def insertAtBeginning(value): 
	new_node = Node(value) 
	if head is None: 
		head = new_node 
		tail = new_node 
	else: 
		new_node.next = head 
		head = new_node
but with sentinel nodes, head and tail always exist, so there is no need for separate case.
def insert_at_beginning(value): 
	new_node = Node(value) 
	new_node.next = head.next 
	head.next = new_node

SLL (Singly Linked List) is where each node only has pointer to the successor element.
runtimes:
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

runtimes:
Access element: O(n) because the computer cannot identify the memory location directly like it can with arrays, although traversal can begin from either the head or tail
Search: O(n) because, in the worst case, we need to inspect every node
Insert: O(1) at the beginning, at the end if a tail pointer is maintained, or before/after a known node; O(n) if the insertion location must first be found
Remove: O(1) from the beginning, from the end if a tail pointer is maintained, or when the node is already known; O(n) if the removal location must first be found
Updating: O(1) if the node is already known; O(n) if the node must first be searched for

Array vs Linked List:













Hashmap: unordered collection of key value pairs (there is no guaranteed order). Known as dictionary in python or swift.
Hashtable: similar to hashmap in the sense that it is an unordered collection of key value pairs but different than hashmap because no null keys or null values and is thread safe
Hashset: unordered collection of unique elements (more specific version of a set)






Stacks and Queues: Container: a data structure that permits storage and retrieval of data items independent of content

Stacks: Retrieval is LIFO Advantage: simple to implement, best to use when retrieval order doesn't matter at all, like processing batch jobs LIFO examples: subway, food in a refrigerator Queue: Retrieval is FIFO Dictionary: Access to data items by content
























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
An algorithm is a procedure that takes any of the possible input instances and transforms it to the desired output. (Skiena, The Algorithm Design Manual)

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

# NC150
N150 (thinking in algorithms): def hasDuplicate(nums: List[int]) -> bool: """ Problem: Check if there is any duplicate in nums Core Idea: Use a set because sets only store unique values Brute Force Algorithm:

Loop through each index i in nums
For each i, loop through every index j after i.
If nums[i] == nums[j]:
return True because we found the same value at two different indexes.
If no matching pair is found:
return False.
for i in range(len(nums)): for j in range(i + 1, len(nums)): if nums[i] == nums[j]: return True return False

i = 0 j = 1 → compare nums[0] and nums[1] j = 2 → compare nums[0] and nums[2] j = 3 → compare nums[0] and nums[3] i = 1 j = 2 → compare nums[1] and nums[2] j = 3 → compare nums[1] and nums[3] i = 2 j = 3 → compare nums[2] and nums[3] i = 3 j loop does not execute because range(4, 4) is empty

Efficient Algorithm:

Convert nums into a set.

This automatically removes duplicate values.
Compare the length of the set with the length of nums.

If the lengths are different:
Return True because at least one duplicate was removed.
Else:
Return False because no duplicates existed.
Why This Works: A set cannot contain duplicate values. So if nums has duplicates, the set will be smaller than nums. If nums has no duplicates, the set and nums will have the same length.

Time Complexity: O(n), because creating the set checks each number once. set(nums) → O(n) len(nums) → O(1) because python stores the length internally

Space Complexity: O(n), because the set stores every number """

def isAnagram(s: str, t: str) -> bool: """ Problem: Given two strings s and t, return True if t is an anagram of s. Otherwise return False Core Idea: Use a hash map to count character frequencies Brute Force Algorithm: sort each string and compare them Efficient Algorithm:

create an empty hash map called count
Loop through each character in s
If the character is already in count:
Increase its frequency by 1.
Else:
Add the character to count with frequency 1.
Loop through each character in t
If the character exists in count:
Decrease its frequency by 1
If the frequency becomes 0
Delete the character key from the count map
Else
Return False because t contains a character that s does not have
After checking all the character in t
If count is empty
Return True
Else
Return False
Optimizations: if the length of s != lenght of t, immediately return false Building a map from the smaller collection can reduce space, but for this it doesn't matter as s and t have to be the same length in the context of anagrams

Why this works: A hashmap stores a frequency of all the characters. If s and t are anagrams, every character count from s should be perfectly canceled out by t. That means the map should be empty at the end.

Time Complexity: O(n + m) as we iterate through both strings

Space Complexity: O(k) where k with the number of unique characters stored in the map """



#Structy
Todo: Sorting Algorithms

M1: Array: -Ordered -Contiguous Fast access, but inserts and deletes can be expensive (insert at beginning or middle is O(n) but at end is O(1) amortized meaning average in the long term) .split in python: breaks string into list of smaller strings based on specified delimiter words = sentence.split(" ")

when looking at whether items satisfy a condition, check for the first item that serves as a counterexample, and return False. If the loop is completed without finding any counterexamples, then function can return True. for item in items: if counter_example_condition: return False return True

or return all(condition for item in collection) like def all_even(nums): return all(num % 2 == 0 for num in nums)

Big O: notation to describe performance of algorithms Time Complexity: how the steps of the algorithm scale with input size Space Complexity: how the space need for the algorithm scales with the input size O(1) < O(logn) < O(n) < O(n^c) < O(c^n) < O(n!)

when using if elif else, it will run the first matching condition, so if one condition is a more specific it should be put first so the wrong condition is not hit

python itertools: module that is part of the standard library for creating iterators (objects that can be looped over) from itertools import combinations def pairs(elements): return [list(pair) for pair in combinations(elements, 2)] or def pairs(elements): result = [] n = len(elements) for i in range(n): for j in range(i + 1, n): result.append([elements[i], elements[j]) return result

i = 0 # "a" j = 1 # "b" ["a","b"] j = 2 # "c" ["a","c"] i = 1 # "b" j = 2 # "c" i = 2 # "c" j = 3 # inner loop doesn't run

HashSets and HashMaps: -Unordered (but in some languages, there could be a guaranteed ordered) -no duplicates for sets

Tradeoff between arrays and sets: array has a linear time lookup but has orderness and duplicates are OK set has a constant time lookup (as well as insert / delete) but does not maintain orderness or duplicates map stores key value pairs and has a constant time lookup by KEY, keys are unordered and cannot be duplicates

def anagrams(s1, s2): char_count = {} if len(s1) != len(s2): return False for c in s1: char_count[c] = char_count.get(c, 0) + 1 for c in s2: if c not in char_count: return False char_count[c] -= 1 if char_count[c] == 0: del char_count[c] return len(char_count) == 0

Defining helper functions: helper functions make it easier to understand what a program is doing because it is a reusable code for a specific task

def char_count(s): # func signature """ before writing the implementation, write the caller and the expected output for clarity """ char_count('cats') # {c: 1, a: 1, t: 1, s: 1}

checking dictionary equality in python means checking that the same keys and values are present

collections module in Python: has specialized container data types

def anagrams(s1, s2): return Counter(s1) == Counter(s2)

def most_frequent_char(s): count = Counter(s) most = None for c in s: if most == None or m[c] > m[most]: most = c return most

tuples in python: immutable ordered list

can be used as dictionary keys rather than lists which cannot since they are mutable (because for hashing to be deterministic it requires the keys to not change)
written with round brackets
if every element in the tuple is hashable then the whole thing is hashable because each will be hashed and then the combine thing will be hashed tuple1 = ("abc", 34, True, 40, "male")
#algorithm: we will construct two sets (we need two sets because each list must be checked against the other) and we will iterate over each list O(n) and see if each element is in the other set O(1) and if not we will append on the result list. O(n) time O(n + m) space def exclusive_items(a, b):   set_a = set(a) # O(n)   set_b = set(b) # O(n)   result = []   for num in b:     if num not in set_a:       result.append(num)   for num in a:     if num not in set_b:       result.append(num)   return result

def all_unique(items):   s = set(items)   return len(s) == len(items)

#algorithm: we will construct counter dictionary and then iterate through each string in the other list (smaller list) and see if the value of that key is greater than zero, and if it is it should append it to a result list, and then decrement from collections import Counter def intersection_with_dupes(a, b):   if len(a) > len(b):     a, b = b, a   count_a = Counter(a)   result = []   for s in b:     if count_a[s] > 0:         result.append(s)         count_a[s] -= 1   return result

def anagrams(s1, s2):   if len(s1) != len(s2):     return False   count = Counter(s1)   for c in s2:     if c not in count:       return False     count[c] -= 1     if count[c] == 0:       del count[c]   return len(count) == 0

recursive functions calls itself def sum_numbers_recursive(numbers): #recursive pattern = sum(x + rest) = x + sum(rest) #base case being empty array if not numbers: return 0 return numbers[0] + sum_numbers_recursive(numbers[1:]) sum_numbers_recursive([4, 2, 7]) = 4 + sum_numbers_recursive([2, 7]) = 2 + sum_numbers_recursive([7]) = 7 + sum_numbers_recursive([]) = 0

Linked List: represents a sequence of nodes, with each node storing data and a pointer to the next node [HEAD] -> [node] -> [node] -> [node] -> [TAIL]

some basic operations adding to the head O(1) because it just rearranges pointers removing from head O(1) for same reason adding to tail O(n) because traversal required O(1) for DLL with tail pointer accessing middle O(n) because no indexing

#algorithm is to maintain a prev, curr, next pointer and for each node save next node, point curr.next to prev and advance prev and curr. when curr is null, prev is the new head of the reversed list def reverse_list(head): prev = None curr = head while curr is not None: next = curr.next curr.next = prev prev = curr curr = next return prev
