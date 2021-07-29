# leetcode

Strategies:
- Sliding Window
- Prefix Sum/Suffix Sum, Prefix Min/Max, Suffix Min/Max
- Interval Problems: use a stack and modify the last stack if overlap, otherwise add it stack.
- Linked List: using a sentinel node.

Data Structures:
- Trie
- Heap
- Binary Index Tree (Fenwick Tree)
- Segment Tree

Python:
- use deque for lists: they have better performance
- SortedList: let's you find elements strictly greater than / less than x in O(log n) time using bisect_left or bisect_right.
- Copy list: `nums[:]`
- list slicing: ok if out of bounds `nums[0:11111]` or `nums[111111:]` they both return empty lists
- this will initialize a matrix: `res = [ [ 0 for i in range(M) ] for j in range(N) ]`

Tips:
- How to check if a number is a decimal? Do n % 1 == 0. That will tell you if it divides evenly by 1 without any remainders.
- With character mappings you need a `s -> t` char mapping AND a `t -> s` char mapping to ensure they map uniquely.
- Refresh your memory how to do binary search
- When dealing with an array of sorted numbers, think about binary search or pointer solutions. Ex: Valid Triangle
- Sum problems: Usually a lookup map of the difference
- Always consider the invariants of your algorithm: what will hold true for your algorithm?
- When facing a problem relating to dependencies or relationships, think about graphs or trees
- When you are really stuck, think about the "reverse" of the problem. For example, if a problem is: "Find add odd numbers", the reverse would be to find even numbers first and anything that is non-even would be the answer!
- When stuck, work backwards from a solution. Assuming you had the solution - how would you move backwards to get to the original problem?

Questions:
- What data type will the input be? Will it always be the same data type?
- Is it possible to get an empty input?
- What is the maximum size of the input?
- If the input is invalid, should the function return 0 or False?
- What data type should the output be?
- Will the input all be in the same case?
- Does punctuation need to be considered?
