# DSA

Basic Data Structures and their runtimes:
Array: a contiguous block of memory that stores a fixed size, indexed collection of same type of data. Same type of data relates to the contiguous nature because every cell must be the same size.
python: arr = []
c++: int arr[]
runtimes:
Access element: O(1) because computer can identify the memory location with simple operation (address = base + (i * size_of_element)) and this is independent of array size hence O(1)
Searching: O(n) because in the worst case it needs to traverse the entire array
Insert/Remove: O(n) if shifting required (for insertion/removal at beginning), O(1) otherwise (insertion/removal at the end)
Updating: O(1)

List: dynamic array (can be resized)

Linked List: non continguous block of memory that stores a node containing a value and pointer to the next node 
runtimes:
Access element: O(n) because computer cannot identify the memory location like it can with arrays
Access element: O(n)
Insert/remove from beginning: O(1)
Insert/remove from end: O(n)
Insert/remove from middle: O(n)


Pass by Value vs Pass by Reference:
Pass by value means copy of data is passed to the function so changes in the function don't affect the original variable
Pass by Reference means reference of the data is passed so changes in the function will affect the other

Pointer vs Reference
Pointer: stores a memory address
Reference: an alias variable 

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

