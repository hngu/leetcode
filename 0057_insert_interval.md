### 57. Insert Interval

Given a set of non-overlapping intervals, insert a new interval into the intervals (merge if necessary).

You may assume that the intervals were initially sorted according to their start times.

**Example 1:**
```
Input: intervals = [[1,3],[6,9]], newInterval = [2,5]
Output: [[1,5],[6,9]]
```

**Example 2:**
```
Input: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]
Output: [[1,2],[3,10],[12,16]]
Explanation: Because the new interval [4,8] overlaps with [3,5],[6,7],[8,10].
```

### Solution:
- once you find an overlap, you will need to create a new interval. Take the current new interval and the overlapping interval and create a new one with the min and max
of those two.
- there is a nice helper function that I found (did not use in the solution below) that will check if two intervals overlap:
```
def do_overlap(interval_1, interval_2):
    front = max(interval_1[0], interval_2[0])
    back = min(interval_1[1], interval_2[1])
    return back - front >= 0 
```
- if touching intervals are not considered overlap, then do `return back - front > 0`.

```
/**
 * @param {number[][]} intervals
 * @param {number[]} newInterval
 * @return {number[][]}
 */
var insert = function(intervals, newInterval) {
    let result = [];
    
    for (let i = 0; i < intervals.length; i++) {
        let interval = intervals[i];
        if (interval[1] < newInterval[0]) {
            result.push(interval);
            continue;
        }
        
        if (newInterval[1] < interval[0]) {
            result.push(newInterval);
            result.push(...intervals.slice(i));
            break;
        }
        
        let min = Math.min(newInterval[0], interval[0]);
        let max = Math.max(newInterval[1], interval[1]);
        newInterval = [min, max];
        
    }
    
    if (!result.length || result[result.length - 1][1] < newInterval[0]) {
        result.push(newInterval);
    }
    
    
    return result;
};
```
