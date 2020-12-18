### 334. Increasing Triplet Subsequence

Given an integer array nums, return true if there exists a triple of indices (i, j, k) such that i < j < k and nums[i] < nums[j] < nums[k]. If no such indices exists, return false.

**Example 1:**
```
Input: nums = [1,2,3,4,5]
Output: true
Explanation: Any triplet where i < j < k is valid.
```

**Example 2:**
```
Input: nums = [5,4,3,2,1]
Output: false
Explanation: No triplet exists.
```

**Example 3:**
```
Input: nums = [2,1,5,0,4,6]
Output: true
Explanation: The triplet (3, 4, 5) is valid because nums[3] == 0 < nums[4] == 4 < nums[5] == 6.
``` 

**Constraints:**
```
1 <= nums.length <= 105
-231 <= nums[i] <= 231 - 1
``` 

Follow up: Could you implement a solution that runs in O(n) time complexity and O(1) space complexity?

### Solution:
```
class Solution:
    def increasingTriplet(self, nums: List[int]) -> bool:
        """
            Idea: set minOne and minTwo to max integer values
            - go through the list:
            -- if the current number is smaller than minOne, then set minOne to it
            -- continue
            -- else if it is smaller than minTwo, then set minTwo to it
            -- continue
            -- else return True 
        """
        minOne = minTwo = sys.maxsize
        
        for num in nums:
            if num < minOne:
                minOne = num
            elif minOne < num < minTwo:
                minTwo = num
            elif minOne < minTwo < num:
                return True
            
        return False
        
```
