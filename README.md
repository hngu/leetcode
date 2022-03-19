# leetcode

Strategies:
- Go with the naive algorithm first! Then think about optimizations.
- Sliding Window
- Prefix/Suffix Sum, Prefix/Suffix Min or Max
- Interval Problems: use a stack and modify the last stack item if overlap, otherwise add it stack.
- Linked List: using a sentinel node.
- Linked List: slow and fast pointer. Have a fast pointer move by 2 while slow pointer goes by 1. OR if you want k difference, move fast pointer to k. Then move them both one by one.
- Backtracking
- Kadane's Algorithm
- Subsequences (Use DP with 2D matrix. Draw the 2D matrix to gain some intuition)
- 2Sum, 3Sum, 4Sum...if looking for indexes, you cannot sort. Otherwise, try sorting if it helps.
- Binary Search
- Subset Generation
- Permutation Generation
- Combination Generation
- Dynamic Programming via Top-Down vs Bottom-Up

Data Structures:
- Trie (you only ever need one trie when solving a problem)
- Heap (given index i, the parent node is `arr[(i - 1) // 2]`, the left node is `arr[(i * 2) + 1]` and the right node is `arr[(i * 2) + 2]`
- Binary Index Tree (Fenwick Tree)
- Segment Tree

Python:
- use deque for lists: they have better performance
- SortedList: let's you find elements strictly greater than / less than x in O(log n) time using bisect_left or bisect_right. Also, when adding or removing an item, it re-sorts.
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
- Power set: for each number, get the subset of the rest of the numbers with and without that number. Think bit flipping.
- Permuations: ordering of elements. Order is important. To generate permutations, for each number pick it then permute the rest of the numbers
- Binary Search Tree stack traversal: store the left side of tree, then pop. If the popped element has a right subtree, store its left side tree.
- First occurrence map: store the first occurence of a number in a map when you iterate over an array. If you see it again, then you can calculate the length between them by taking `i - map[num]`
- 2D array backtracking: for word search, have a global 2D visited matrix. In a for loop, set the visited cell to True and recurse. At the end of the recurse before the loop ends, set the visited cell back to False.
- Another example of backtracking is course scheduling and topsort. For example, you can have a visited array when processing a course and its prerequisites. If there is a cycle, that visited array should have it set to true. Once you process a course and prereqs, then set the visited at the end of the loop to False.
- DP Grid area calculations: see if a cell's DP can be calculated from its neighboring cells. For example: `dp[i][j] = min(dp[above it], dp[left of it], dp[diagnoal))`
- Problems where it asks you to solve it in constant space and in linear time: try modifying the original array. Use markers like setting a number to a negative.
- 4Sum: two O(n^2) loops with map: one for a + b and the other for c + d.
- Monotonic stacks are a good option when a problem involves comparing the size of numeric elements, with their order being relevant.
- Another example usage of monotonic stack is removing k digits.
- Any manual math calculations: move backwards and always consider carries! At the end of the loop do one final computation for carries.
- Be careful of parsing strings that contains numbers. A number can be multidigit like: `123+456`
- Word ladder hard: create a graph using a hashmap of pattern -> list of candidates like: `patterns[h*t] = [hot, hit]`. Also, you can use the count data structure as a way to check if you visited a node and skip processing.
- Stack trick: you can use a counter to store relative order of elements. When an element is pushed, it will always have a higher counter than any other element that is already pushed in the stack. This can be useful in storing elements from a stack in a heap.

Questions:
- What data type will the input be? Will it always be the same data type?
- Is it possible to get an empty input?
- What is the maximum size of the input?
- If the input is invalid, should the function return 0 or False?
- What data type should the output be?
- Will the input all be in the same case?
- Does punctuation need to be considered?
