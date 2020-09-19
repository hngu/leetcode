### 42. Trapping Rain Water

Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.

The above elevation map is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped. Thanks Marcos for contributing this image!

**Example:**
```
Input: [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
```

### Solution:
- My solution TLE because I was slicing arrays to find the max.
- I revised my solution based on their suggestion of iteratively finding the left and right max.

```
/**
 * @param {number[]} height
 * @return {number}
 */
var trap = function(height) {
    let maxLeftWalls = [];
    let maxRightWalls = [];
    let leftMax = height[0];
    let rightMax = height[height.length - 1];
    
    for (let i = 0; i < height.length; i++) {
        leftMax = Math.max(leftMax, height[i]);
        maxLeftWalls.push(leftMax);
    }
    
    for (let i = height.length - 1; i >= 0; i--) {
        rightMax = Math.max(rightMax, height[i]);
        maxRightWalls.unshift(rightMax);
    }    
    
    let total = 0;
    
    for (let i = 0; i < height.length; i++) {
        let current = height[i];
        let left = maxLeftWalls[i];
        let right = maxRightWalls[i];
        
        if (left < current || right < current) {
            continue;
        }
        
        let min = Math.min(left, right);
        total += min - current;
    }
    
    return total;
};
```
