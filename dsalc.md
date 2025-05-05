# DSA

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




# LC75
