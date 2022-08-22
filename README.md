# leetcode

A collection of leetcode problems written in JavaScript or Python.

## Overall Approach

- Go with the naive algorithm first! You want to gain some intuition and make sure you understand the problem fully.
- Then think about optimizations.
- Ask the interviewer if you are on the right path. Asking for hints if necessary.
- Think about various inputs and outputs. Think about edge cases as well. Examples include - empty string, 0, false, weird punctuations for string problems, Large inputs, small inputs, etc.
- Write up psuedocode if necessary to convey your idea to the interviewer. That way, the interviewer can verify your high level solution before implementation.
- After you finish coding the solution, test it out.
- Finally, examine the space and time complexity of your solution.

## Topics

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
