### 1446. Consecutive Characters

Given a string s, the power of the string is the maximum length of a non-empty substring that contains only one unique character.

Return the power of the string.

**Example 1:**
```
Input: s = "leetcode"
Output: 2
Explanation: The substring "ee" is of length 2 with the character 'e' only.
```

**Example 2:**
```
Input: s = "abbcccddddeeeeedcba"
Output: 5
Explanation: The substring "eeeee" is of length 5 with the character 'e' only.
```

**Example 3:**
```
Input: s = "triplepillooooow"
Output: 5
```

**Example 4:**
```
Input: s = "hooraaaaaaaaaaay"
Output: 11
```

**Example 5:**
```
Input: s = "tourist"
Output: 1
``` 

**Constraints:**
```
1 <= s.length <= 500
s contains only lowercase English letters.
```

### Solution:

```
class Solution:
    def maxPower(self, s: str) -> int:
        """
            Cannot use a hashmap because it does not take into account
            consecutive length.
            
            set maxCount = 0
            set count = 0
            for each char in s:
            set comparisonChar to char if it is null
            if comparsionChar == char, increment count
            else set comparisonChar to char
            maxCount = max(count, maxCount)
            count = 0
            
            IMPORTANT: do maxCount = max(count, maxCount)
            in the end in case the string is "aaaa" and never sets
            maxCount in the else
        """
        maxCount = 0
        count = 0
        comparisonChar = None
        
        for char in s:
            if comparisonChar is None:
                comparisonChar = char

            if comparisonChar == char:
                count += 1
                continue
            else:
                comparisonChar = char
                maxCount = max(count, maxCount)
                count = 1
        
        # so dumb! there might not be a change in chars
        # so need to update maxCount if it never goes 
        # to the else above!
        maxCount = max(maxCount, count)
        return maxCount
        
```
