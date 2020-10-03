### 532. K-diff Pairs in an Array

Given an array of integers nums and an integer k, return the number of unique k-diff pairs in the array.

A k-diff pair is an integer pair (nums[i], nums[j]), where the following are true:
```
0 <= i, j < nums.length
i != j
a <= b
b - a == k
```
**Example 1:**
```
Input: nums = [3,1,4,1,5], k = 2
Output: 2
Explanation: There are two 2-diff pairs in the array, (1, 3) and (3, 5).
Although we have two 1s in the input, we should only return the number of unique pairs.
```

**Example 2:**
```
Input: nums = [1,2,3,4,5], k = 1
Output: 4
Explanation: There are four 1-diff pairs in the array, (1, 2), (2, 3), (3, 4) and (4, 5).
```

**Example 3:**
```
Input: nums = [1,3,1,5,4], k = 0
Output: 1
Explanation: There is one 0-diff pair in the array, (1, 1).
```

**Example 4:**
```
Input: nums = [1,2,4,4,3,3,0,9,2,3], k = 3
Output: 2
```

**Example 5:**
```
Input: nums = [-1,-2,-3], k = 1
Output: 2
```

### Solution:
- What i did was create a map of numbers to the list of numbers themselves.
- Then I iterate through the numbers and add k to each number. If the sum appears in the map, then it is a legit pair. Add it to the set.
- Watch out: if k = 0 and the nums is: [1,2,3,4,5], you can't say [1, 1]. So be careful of that! (I luckily was aware of this)
- **Another Way** is to sort the array (n log n) then for each num in nums, find num + k using binary search. Binary search is (log n) and doing it for each number is n log n
but with constant space.

```
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findPairs = function(nums, k) {
    let map = {};
    let result = new Set();
    
    nums.forEach(num => {
        map[num] = map[num] || [];
        map[num].push(num);
    });
    
    nums.forEach(num => {
        let sum = num + k;
        
        if (map[num] !== undefined && map[sum] !== undefined) {
            if (num === sum && map[num].length <= 1) {
                return;
            }
            
            let ans = `${num}_${sum}`;
            result.add(ans);
        }
    });
    
    return result.size;
};
```
