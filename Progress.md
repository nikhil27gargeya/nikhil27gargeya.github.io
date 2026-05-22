# Progress

M1:
Structy:
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


