### 129. Sum Root to Leaf Numbers

Given a binary tree containing digits from 0-9 only, each root-to-leaf path could represent a number.

An example is the root-to-leaf path 1->2->3 which represents the number 123.

Find the total sum of all root-to-leaf numbers.

Note: A leaf is a node with no children.

**Example:**
```
Input: [1,2,3]
    1
   / \
  2   3
Output: 25
Explanation:
The root-to-leaf path 1->2 represents the number 12.
The root-to-leaf path 1->3 represents the number 13.
Therefore, sum = 12 + 13 = 25.
```

**Example 2:**
```
Input: [4,9,0,5,1]
    4
   / \
  9   0
 / \
5   1
Output: 1026
Explanation:
The root-to-leaf path 4->9->5 represents the number 495.
The root-to-leaf path 4->9->1 represents the number 491.
The root-to-leaf path 4->0 represents the number 40.
Therefore, sum = 495 + 491 + 40 = 1026.
```

### Solution:
- GOTCHA: need to do parseInt base 10 in case of leading zeroes!
- Create helper function that takes in a node and list of numbers
- If I am null, then return list of numbers to a global result array
- If I am not null, create two new arrays: one for left traversal and one for right traversal
- Recurse with helper using node.left or node.right and the new arrays
- Sum up the global array and return result

```
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
var sumNumbersHelper = function(node, tuple) {
    let sum = tuple[0];
    let digits = tuple[1];
    
    if (!node.left && !node.right) {
        // must be leaf node
        digits.push(node.val);
        sum += parseInt(digits.join(''), 10);
        return sum;
    }
    
    let leftSum = 0;
    let rightSum = 0;
    
    if (node.left) {
        leftSum = sumNumbersHelper(node.left, [sum, [...digits, node.val]]);
    }
    
    if (node.right) {
        rightSum = sumNumbersHelper(node.right, [sum, [...digits, node.val]]);
    }
    
    return leftSum + rightSum;
    
    
}
var sumNumbers = function(root) {
    if (!root) {
        return 0;
    }
    
    return sumNumbersHelper(root, [0, []]);
};
```
