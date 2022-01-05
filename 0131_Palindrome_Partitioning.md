### 131. Palindrome Partitioning
Medium

Given a string s, partition s such that every substring of the partition is a palindrome. Return all possible palindrome partitioning of s.

A palindrome string is a string that reads the same backward as forward. 

**Example 1:**
```
Input: s = "aab"
Output: [["a","a","b"],["aa","b"]]
```

**Example 2:**
```
Input: s = "a"
Output: [["a"]]
``` 

**Constraints:**
```
1 <= s.length <= 16
s contains only lowercase English letters.
```

**Tags**
- Revisit
- palindrome

### Solution
```
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        """
            Build lookup matrix of start, end is a palindrome
        """
        ans = []
        length = len(s)
        lookup = [[False for _ in range(length)] for _ in range(length)]
        
        for i in range(0, length):
            for j in range(i, length):
                substring = s[i:j + 1]
                if substring == substring[::-1]:
                    lookup[i][j] = True
        
        
        def recurse(index):
            if index == length:
                return [[]]
            
            partitions = []
            for i in range(index, length):
                if not lookup[index][i]:
                    continue
                    
                result = recurse(i + 1)
               
                if result is not None:
                    for part in result:
                        partitions.append([s[index:i + 1]] + part)
            
            
            if not partitions:
                return None
            
            return partitions
        
        
        return recurse(0)
                
        
        
        
```
