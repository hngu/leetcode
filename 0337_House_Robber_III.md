### 337. House Robber III
Medium

The thief has found himself a new place for his thievery again. There is only one entrance to this area, called root.

Besides the root, each house has one and only one parent house. After a tour, the smart thief realized that all houses in this place form a binary tree. It will automatically contact the police if two directly-linked houses were broken into on the same night.

Given the root of the binary tree, return the maximum amount of money the thief can rob without alerting the police. 

**Example 1:**
```
   3
2     3
  3     1
 
Input: root = [3,2,3,null,3,null,1]
Output: 7
Explanation: Maximum amount of money the thief can rob = 3 + 3 + 1 = 7.
```

**Example 2:**
```
    3
  4     5
1   3     1

Input: root = [3,4,5,1,3,null,1]
Output: 9
Explanation: Maximum amount of money the thief can rob = 4 + 5 = 9.
``` 

**Constraints:**
```
The number of nodes in the tree is in the range [1, 10^4].
0 <= Node.val <= 10^4
```

**Tags**
- Revisit
- Dynamic Programming

### Solution
- My solution uses recursion with DP memoization.
- There is a bottom up solution
```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def rob(self, root: Optional[TreeNode]) -> int:
        """
            Top down DP
            rob root + children's children
            or rob children
        """
        dp = {}
        def helper(node, index=1):
            if not node:
                return 0

            if dp.get(index):
                return dp[index]
            
            # rob root
            root_value = node.val
            if node.left:
                root_value += helper(node.left.left, index * 2 * 2)
                root_value += helper(node.left.right, index * 2 * 2 + 1)
            if node.right:
                root_value += helper(node.right.left, (index * 2 + 1) * 2)
                root_value += helper(node.right.right, (index * 2 + 1) * 2 + 1)

            # rob children
            children_value = helper(node.left, index * 2) + helper(node.right, index * 2 + 1)

            dp[index] = max(root_value, children_value)
            return dp[index]

        return helper(root)
        
```
