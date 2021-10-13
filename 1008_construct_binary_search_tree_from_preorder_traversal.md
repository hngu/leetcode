### 1008. Construct Binary Search Tree from Preorder Traversal

Return the root node of a binary search tree that matches the given preorder traversal.

(Recall that a binary search tree is a binary tree where for every node, any descendant of node.left has a value < node.val, and any descendant of node.right has a value > node.val.  Also recall that a preorder traversal displays the value of the node first, then traverses node.left, then traverses node.right.)

It's guaranteed that for the given test cases there is always possible to find a binary search tree with the given requirements.

**Example 1:**
```
Input: [8,5,1,7,10,12]
Output: [8,5,10,1,7,null,12]

    8
  5   10
1   7   12
``` 

**Constraints:**
```
1 <= preorder.length <= 100
1 <= preorder[i] <= 10^8
The values of preorder are distinct.
```

**Tags**
- Trees
- Revisit
- Need to account for no split point!

### Solution:
```
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {number[]} preorder
 * @return {TreeNode}
 */
var bstFromPreorder = function(preorder) {
    // if preorder is empty, return null
    if (!preorder.length) {
        return null;
    }
    // first get dequeue the first node, that should be root
    let root = preorder.shift();
    let splitPoint = 0;
    
    // then find the first set of nodes that are less than me, call that small set
    // then find the second set of nodes that are greater than me, call that big set
    for (let i = 0; i < preorder.length; i++) {
        if (preorder[i] < root) {
            splitPoint++;
        } else {
            break;
        }
    }
    let smallSet = preorder.slice(0, splitPoint);
    let bigSet = preorder.slice(splitPoint);
    
    
    // then call bstFromPreorder(smallSet) and store that as left tree
    let leftTree = bstFromPreorder(smallSet);
    // then call bstFromPreorder(bigSet) and store that as right tree
    let rightTree = bstFromPreorder(bigSet);
    // create root node
    root = new TreeNode(root);
    
    // root.left = leftTree
    root.left = leftTree;
    // root.right = rightTree
    root.right = rightTree;
    // return root
    return root;
};
```
Python Solution
```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def bstFromPreorder(self, preorder: List[int]) -> Optional[TreeNode]:
        if not preorder:
            return None
        
        num = preorder.pop(0)
        root = TreeNode(num)
        
        if not preorder:
            return root

        split = None
        
        for index, n in enumerate(preorder):
            if n > num:
                split = index
                break
        
        if split is None:
            root.left = self.bstFromPreorder(preorder)
            return root
    
        root.left = self.bstFromPreorder(preorder[:split])
        root.right = self.bstFromPreorder(preorder[split:])
        
        return root
        
    
        
```
