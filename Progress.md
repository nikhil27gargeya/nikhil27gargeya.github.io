# Progress

M1:
Array: 
-Ordered
-Contiguous
Fast access, but inserts and deletes can be expensive
.split in python: breaks string into list of smaller strings based on specified delimiter
words = sentence.split(" ")

when looking at whether items satisfy a condition, check for the first item that serves as a counterexample, and return False. If the loop is completed without finding any counterexamples, then function can return True.
for item in items:
  if counter_example_condition:
      return False
return True

or return all(condition for item in collection)
like def all_even(nums): return all(num % 2 == 0 for num in nums)

Big O: notation to describe performance of algorithms 
Time Complexity: how the steps of the algorithm scale with input size
Space Complexity: how the space need for the algorithm scales with the input size
O(1) < O(logn) < O(n) < O(n^c) < O(c^n) < O(n!)

when using if elif else, it will run the first matching condition, so if one condition is a more specific it should be put first so the wrong condition is not hit

python itertools: module that is part of the standard library for creating iterators (objects that can be looped over)
from itertools import combinations
def pairs(elements):
    return [list(pair) for pair in combinations(elements, 2)]
or
def pairs(elements):
  result = []
  n = len(elements)
  for i in range(n):
     for j in range(i + 1, n):
         result.append([elements[i], elements[j])
  return result

i = 0 # "a"
j = 1 # "b"
["a","b"]
j = 2 # "c"
["a","c"]
i = 1 # "b"
j = 2 # "c"
i = 2 # "c"
j = 3 # inner loop doesn't run

HashSets and HashMaps:
-Unordered (but in some languages, there could be a guaranteed ordered)
-no duplicates for sets

Tradeoff between arrays and sets:
array has a linear time lookup but has orderness and duplicates are OK
set has a constant time lookup (as well as insert / delete) but does not maintain orderness or duplicates
map stores key value pairs and has a constant time lookup by KEY, keys are unordered and cannot be duplicates

def anagrams(s1, s2):
    char_count = {}
    if len(s1) != len(s2):
        return False
    for c in s1:
        char_count[c] = char_count.get(c, 0) + 1
    for c in s2:
        if c not in char_count: 
            return False
        char_count[c] -= 1
        if char_count[c] == 0:
            del char_count[c]
    return len(char_count) == 0

Defining helper functions:
helper functions make it easier to understand what a program is doing because it is a reusable code for a specific task

def char_count(s): # func signature
""" 
before writing the implementation, write the caller and the expected output for clarity
"""
char_count('cats') # {c: 1, a: 1, t: 1, s: 1}

checking dictionary equality in python means checking that the same keys and values are present

collections module in Python: has specialized container data types

def anagrams(s1, s2):
    return Counter(s1) == Counter(s2)

def most_frequent_char(s):
  count = Counter(s)
  most = None
  for c in s:
    if most == None or m[c] > m[most]:
      most = c
  return most
      
tuples in python: immutable ordered list
- can be used as dictionary keys rather than lists which cannot since they are mutable (because for hashing to be deterministic it requires the keys to not change)
- written with round brackets
- if every element in the tuple is hashable then the whole thing is hashable because each will be hashed and then the combine thing will be hashed
tuple1 = ("abc", 34, True, 40, "male")









