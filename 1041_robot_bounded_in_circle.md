### 1041. Robot Bounded In Circle

On an infinite plane, a robot initially stands at (0, 0) and faces north.  The robot can receive one of three instructions:

"G": go straight 1 unit;
"L": turn 90 degrees to the left;
"R": turn 90 degress to the right.
The robot performs the instructions given in order, and repeats them forever.

Return true if and only if there exists a circle in the plane such that the robot never leaves the circle.

**Example 1:**
```
Input: "GGLLGG"
Output: true
Explanation: 
The robot moves from (0,0) to (0,2), turns 180 degrees, and then returns to (0,0).
When repeating these instructions, the robot remains in the circle of radius 2 centered at the origin.
```

**Example 2:**
```
Input: "GG"
Output: false
Explanation: 
The robot moves north indefinitely.
```

**Example 3:**
```
Input: "GL"
Output: true
Explanation: 
The robot moves from (0, 0) -> (0, 1) -> (-1, 1) -> (-1, 0) -> (0, 0) -> ...
```

**Note:**
```
1 <= instructions.length <= 100
instructions[i] is in {'G', 'L', 'R'}
```

### Solution:
The problem gave two hints that was SUPER HELPFUL:
- Calculate the final vector of how the robot travels after executing all instructions once - it consists of a change in position plus a change in direction.
- The robot stays in the circle iff (looking at the final vector) it changes direction (ie. doesn't stay pointing north), or it moves 0.

It wasn't as bad as I thought it was once you have those hints. You don't have to worry about the "length" or "size" of the vector unless it is zero.
If it is a non-zero vector change, and the direction is not NORTH, the robot will definitely be in a bounded circle. Because it is turning at the end 
of each set of instructions and the vector change is static after each set of instructions so eventually it will circle around.

```
/**
 * @param {string} instructions
 * @return {boolean}
 */
var isRobotBounded = function(instructions) {
    let current = [0, 0];
    let direction = 'N';
    
    for (let i = 0; i < instructions.length; i++) {
        let instruction = instructions[i];
        if (instruction === 'G') {
            switch(direction) {
                case 'N':
                    current[1] += 1;
                    break;
                case 'S':
                    current[1] -= 1;
                    break;  
                case 'E':
                    current[0] += 1;
                    break;
                case 'W':
                    current[0] -= 1;
                    break;
            }
        } else if (instruction === 'L') {
            direction = direction === 'N' ? 'W' : direction === 'W' ? 'S' : direction === 'S' ? 'E' : 'N';
        } else {
            direction = direction === 'N' ? 'E' : direction === 'E' ? 'S' : direction === 'S' ? 'W' : 'N';            
        }
    }
    
    if (current[0] === 0 && current[1] === 0) {
        return true;
    }
    
    if (direction !== 'N') {
        return true;
    }
    
    return false;
};
```
