### 1239. Maximum Length of a Concatenated String with Unique Characters
Medium

Given an array of strings arr. String s is a concatenation of a sub-sequence of arr which have unique characters.

Return the maximum possible length of s. 

**Example 1:**
```
Input: arr = ["un","iq","ue"]
Output: 4
Explanation: All possible concatenations are "","un","iq","ue","uniq" and "ique".
Maximum length is 4.
```

**Example 2:**
```
Input: arr = ["cha","r","act","ers"]
Output: 6
Explanation: Possible solutions are "chaers" and "acters".
```

**Example 3:**
```
Input: arr = ["abcdefghijklmnopqrstuvwxyz"]
Output: 26
``` 

**Constraints:**
```
1 <= arr.length <= 16
1 <= arr[i].length <= 26
arr[i] contains only lower case English letters.
```

### Solution
```
class Solution:
    def maxLength(self, arr: List[str]) -> int:
        """
            Let's first generate the combinations naively
            Then get the max of the unique characters
        """
        max_length = 0
        
        def helper(arr, result):
            nonlocal max_length
            if not arr:
                if result:
                    result = "".join(result)
                    if len(result) == len(set(list(result))):
                        max_length = max(max_length, len(result)) 
                return
            
            # get words without the first word
            helper(arr[1:], result)
            
            # get words with the first word
            helper(arr[1:], result + [arr[0]])
    
    
        helper(arr, [])
        
        return max_length

        
        
```
