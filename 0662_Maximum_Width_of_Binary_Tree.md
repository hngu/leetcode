### 662. Maximum Width of Binary Tree
Medium

Given the root of a binary tree, return the maximum width of the given tree.

The maximum width of a tree is the maximum width among all levels.

The width of one level is defined as the length between the end-nodes (the leftmost and rightmost non-null nodes), where the null nodes between the end-nodes are also counted into the length calculation.

It is guaranteed that the answer will in the range of 32-bit signed integer. 

**Example 1:**
```
Input: root = [1,3,2,5,3,null,9]
Output: 4
Explanation: The maximum width existing in the third level with the length 4 (5,3,null,9).
```

**Example 2:**
```
Input: root = [1,3,null,5,3]
Output: 2
Explanation: The maximum width existing in the third level with the length 2 (5,3).
```

**Example 3:**
```
Input: root = [1,3,2,5]
Output: 2
Explanation: The maximum width existing in the second level with the length 2 (3,2).
``` 

**Constraints:**
```
The number of nodes in the tree is in the range [1, 3000].
-100 <= Node.val <= 100
```

**Tags**
- Revisit
- Binary tree

### Solution
- Because null nodes between the left most and right most nodes at each level count as part of the width, the simplest thing we can do is use BFS and indexing
- Each node will have an index. If node has index i, then the left node has 2i + 1 and right node has 2i + 2.
- At each iteration of the BFS, we take the index of the last node - index of first node + 1 to calculate the width
```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def widthOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        max_width = 0
        queue = collections.deque([(root, 1)])
        
        def get_width(queue):    
            return queue[-1][1] - queue[0][1] + 1
        
        while queue:
            temp = collections.deque([])
            max_width = max(max_width, get_width(queue))
            while queue:
                node, count = queue.popleft()
                if not node:
                    continue
                if node.left:
                    temp.append((node.left, count * 2))
                if node.right:
                    temp.append((node.right, count * 2 + 1))
            queue = temp
        
        return max_width
        
```