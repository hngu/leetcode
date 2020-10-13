### 148. Sort List

Given the head of a linked list, return the list after sorting it in ascending order.

Follow up: Can you sort the linked list in O(n logn) time and O(1) memory (i.e. constant space)? 

**Example 1:**
```
4 -> 2 -> 1 -> 3
Input: head = [4,2,1,3]
Output: [1,2,3,4]
```

**Example 2:**
```
-1 -> 5 -> 3 -> 4 -> 0
Input: head = [-1,5,3,4,0]
Output: [-1,0,3,4,5]
```

**Example 3:**
```
Input: head = []
Output: []
``` 

**Constraints:**
```
The number of nodes in the list is in the range [0, 5 * 104].
-105 <= Node.val <= 105
```

### Solution:
- My solution did not take constant space. It takes O(n) space.
- To take constant space, you have to merge sort the lists.

```
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var sortList = function(head) {
    // iterate through the list and put in an array
    // then sort the array by value
    // then for each item in array:
    // set the next point to its next item
    // return the first element in the array
    
    let list = [];
    let current = head;
    
    while (current) {
        list.push(current);
        current = current.next;
    }
    
    list = list.sort((a, b) => {
        return a.val - b.val;
    });
    
    for (let i = 0; i < list.length; i++) {
        let node = list[i];
        let nextNode = list[i + 1] ? list[i + 1] : null;
        node.next = nextNode;
    }
    
    if (list.length) {
        return list[0];
    }
    
    return null;
};
```
