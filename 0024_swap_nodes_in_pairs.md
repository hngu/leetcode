### 24. Swap Nodes in Pairs

Given a linked list, swap every two adjacent nodes and return its head.

You may not modify the values in the list's nodes. Only nodes itself may be changed. 

**Example 1:**
```
1 -> 2 -> 3 -> 4
2 -> 1 -> 4 -> 3

Input: head = [1,2,3,4]
Output: [2,1,4,3]
```

**Example 2:**
```
Input: head = []
Output: []
```

**Example 3:**
```
Input: head = [1]
Output: [1]
``` 

**Constraints:**
```
The number of nodes in the list is in the range [0, 100].
0 <= Node.val <= 100
```

### Solution:
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def swapPairs(self, head: ListNode) -> ListNode:
        left = None
        current = head
        if not current or not current.next:
            return current
        right = current.next
        newHead = None
        
        while right:
            temp = right.next
            right.next = current
            current.next = temp
            
            if left:
                left.next = right
                
            if not newHead:
                newHead = right
            
            # switch positions to correct current and right
            temp = right
            right = current
            current = temp
            
            # then move pointers if you can
            if not left:
                left = current
            else:
                left = left.next
            right = right.next
            current = current.next
            
            if right:
                right = right.next
                current = current.next
                left = left.next
            
            
        return newHead
        
```
