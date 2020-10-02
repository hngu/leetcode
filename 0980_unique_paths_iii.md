### 980. Unique Paths III

On a 2-dimensional grid, there are 4 types of squares:

1 represents the starting square.  There is exactly one starting square.
2 represents the ending square.  There is exactly one ending square.
0 represents empty squares we can walk over.
-1 represents obstacles that we cannot walk over.
Return the number of 4-directional walks from the starting square to the ending square, that walk over every non-obstacle square exactly once. 

**Example 1:**
```
Input: [[1,0,0,0],[0,0,0,0],[0,0,2,-1]]
Output: 2
Explanation: We have the following two paths: 
1. (0,0),(0,1),(0,2),(0,3),(1,3),(1,2),(1,1),(1,0),(2,0),(2,1),(2,2)
2. (0,0),(1,0),(2,0),(2,1),(1,1),(0,1),(0,2),(0,3),(1,3),(1,2),(2,2)
```

**Example 2:**
```
Input: [[1,0,0,0],[0,0,0,0],[0,0,0,2]]
Output: 4
Explanation: We have the following four paths: 
1. (0,0),(0,1),(0,2),(0,3),(1,3),(1,2),(1,1),(1,0),(2,0),(2,1),(2,2),(2,3)
2. (0,0),(0,1),(1,1),(1,0),(2,0),(2,1),(2,2),(1,2),(0,2),(0,3),(1,3),(2,3)
3. (0,0),(1,0),(2,0),(2,1),(2,2),(1,2),(1,1),(0,1),(0,2),(0,3),(1,3),(2,3)
4. (0,0),(1,0),(2,0),(2,1),(1,1),(0,1),(0,2),(0,3),(1,3),(1,2),(2,2),(2,3)
```

**Example 3:**
```
Input: [[0,1],[2,0]]
Output: 0
Explanation: 
There is no path that walks over every empty square exactly once.
Note that the starting and ending square can be anywhere in the grid.
``` 

**Note:**
```
1 <= grid.length * grid[0].length <= 20
```

### Solution:
- Whenever we see the context of grid traversal, the technique of backtracking or DFS (Depth-First Search) should ring a bell. Maybe DP as well.
- Use backtracking!
- I messed up on kicking off the helper, miscounting the number of zeroes, passing `coord[i], coord[j]` into the helper function inside nextPaths forEach
- Also, return once you find 2.
- I also terminated too early: if there are no zeroes, doesn't mean a path [[1,2]] does not exist. The answer in that scenario is 1!

```
/**
 * @param {number[][]} grid
 * @return {number}
 */
var uniquePathsIII = function(grid) {
    // count number of zeroes
    let numZeroes = 0;
    let startCoord = [];
    
    for (let i = 0; i < grid.length; i++) {
        let row = grid[i];
        for (let j = 0; j < row.length; j++) {
            let cell = grid[i][j];
            if (cell === 0) {
                numZeroes += 1;
            }
            if (cell === 1) {
                startCoord = [i, j];
            }
        }
    }
    
    let pathes = 0;
    
    let helper = (i, j, path) => {
        if (grid[i][j] === 2 && path.length === numZeroes + 2) {
            pathes += 1;
            return;
        }
        
        let nextPaths = [];
        if (grid[i - 1] && grid[i - 1][j] !== undefined && grid[i - 1][j] !== -1 &&
            !path.find(coord => coord[0] === i - 1 && coord[1] === j)) {
            nextPaths.push([i - 1, j]);
        }
        if (grid[i + 1] && grid[i + 1][j] !== undefined && grid[i + 1][j] !== -1 &&
            !path.find(coord => coord[0] === i + 1 && coord[1] === j)) {
            nextPaths.push([i + 1, j]);
        }
        if (grid[i] && grid[i][j - 1] !== undefined && grid[i][j - 1] !== -1 &&
            !path.find(coord => coord[0] === i && coord[1] === j - 1)) {
            nextPaths.push([i, j - 1]);
        }
        if (grid[i] && grid[i][j + 1] !== undefined && grid[i][j + 1] !== -1 &&
            !path.find(coord => coord[0] === i && coord[1] === j + 1)) {
            nextPaths.push([i, j + 1]);
        }        
        nextPaths.forEach(coord => {
            let newPath = [...path, coord];
            helper(coord[0], coord[1], newPath);
        });
    };
    
    helper(startCoord[0], startCoord[1], [startCoord]);
    
    return pathes;
};
```
