# leetcode

Strategies:
- Sliding Window
- Prefix Sum/Suffix Sum
- Interval Problems: use a stack and modify the last stack if overlap, otherwise add it stack.
- Linked List: using a sentinel node.
- With character mappings you need a `s -> t` char mapping AND a `t -> s` char mapping to ensure they map uniquely.

Data Structures:
- Trie
- Heap
- Binary Index Tree (Fenwick Tree)
- Segment Tree

Python:
- use deque for lists: they have better performance
- SortedList: let's you find elements strictly greater than / less than x in O(log n) time using bisect_left or bisect_right.

Tips:
- How to check if a number is a decimal? Do n % 1 == 0. That will tell you if it divides evenly by 1 without any remainders.
