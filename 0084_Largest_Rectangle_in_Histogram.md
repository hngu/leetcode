### 84. Largest Rectangle in Histogram
Hard

Given an array of integers heights representing the histogram's bar height where the width of each bar is 1, return the area of the largest rectangle in the histogram.

**Example 1:**
```

      +
    + +
    + +
    + +   +
+   + + + +
+ + + + + +

Input: heights = [2,1,5,6,2,3]
Output: 10
Explanation: The above is a histogram where width of each bar is 1.
The largest rectangle is shown in the red area, which has an area = 10 units.
```

**Example 2:**
```

  +
  +
+ +
+ +
Input: heights = [2,4]
Output: 4
``` 

**Constraints:**
```
1 <= heights.length <= 10^5
0 <= heights[i] <= 10^4
```

**Tags**
- Revisit
- unsolved
- stack

### Solution
Brute Force
- The brute force is to calculate the max area between each pair of column from i -> j while also taking into account that there is a min height between i and j.
- For each i:
- min height = i
- for each j where j >= i:
- min height = min(min_height, j)
- max area = max(max_area, min_height * (j - i + 1))
- But this is O(n^2) which is too slow
