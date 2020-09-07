### 189. Rotate Array

Given an array, rotate the array to the right by k steps, where k is non-negative.

Follow up:

Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.
Could you do it in-place with O(1) extra space?
 
**Example 1:**
```
Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
```

**Example 2:**
```
Input: nums = [-1,-100,3,99], k = 2
Output: [3,99,-1,-100]
Explanation: 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
``` 

**Constraints:**
- 1 <= nums.length <= 2 * 10^4
- It's guaranteed that nums[i] fits in a 32 bit-signed integer.
- k >= 0

### Solution:

I did not use this solution, but you can do this:
- Reverse all the numbers: [7,6,5,4,3,2,1]
- Reverse the first k numbers: [5,6,7,4,3,2,1]
- Reverse the rest of the numbers: [5,6,7,1,2,3,4]

```
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var rotate = function(nums, k) {
    if (nums.length === 0 || k === 0) {
        return;
    }
     
    let rotations = k % nums.length;
    
    while(rotations > 0) {
        let num = nums.pop();
        nums.unshift(num);
        rotations -= 1;
    }
};
```
