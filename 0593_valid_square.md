### 593. Valid Square

Given the coordinates of four points in 2D space, return whether the four points could construct a square.

The coordinate (x,y) of a point is represented by an integer array with two integers.

**Example:**
```
Input: p1 = [0,0], p2 = [1,1], p3 = [1,0], p4 = [0,1]
Output: True
``` 

**Note:**
```
All the input integers are in the range [-10000, 10000].
A valid square has four equal sides with positive length and four equal angles (90-degree angles).
Input points have no order.
``` 

### Solution:
Mistakes:
- I need to check all the points!
- The distance formula is sqrt((x2 - x1) ^ 2 + (y2 - y1) ^2)
- There are some precision errors so I compared diagonals with each other.
```
class Solution:
    def validSquare(self, p1: List[int], p2: List[int], p3: List[int], p4: List[int]) -> bool:
        """
            For each point:
            - Find two other points that have the same length
            - AND form a 90 deg angle, using pythageoran theorem
            - If not found, return False
            
            Return True
        """
        def getDistance(p1, p2):
            rise = (p2[1] - p1[1]) ** 2
            run = (p2[0] - p1[0]) ** 2
            return sqrt(rise + run)
        
        def isValid(p1, p2, p3, p4):
            dist1 = getDistance(p1, p2)
            dist2 = getDistance(p1, p3)
            dist3 = getDistance(p1, p4)
            
            if dist1 <= 0 or dist2 <= 0 or dist3 <= 0:
                return False
            
            if dist1 == dist2 and dist3 == getDistance(p2, p3):
                return True
            if dist1 == dist3 and dist2 == getDistance(p2, p4):
                return True
            if dist2 == dist3 and dist1 == getDistance(p3, p4):
                return True
            
            return False
        
        return all([
            isValid(p1, p2, p3, p4),
            isValid(p2, p1, p3, p4),
            isValid(p3, p2, p1, p4),
            isValid(p4, p2, p3, p1)
        ])
            
        
```
