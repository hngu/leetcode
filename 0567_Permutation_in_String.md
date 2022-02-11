### 567. Permutation in String
Medium

Given two strings s1 and s2, return true if s2 contains a permutation of s1, or false otherwise.

In other words, return true if one of s1's permutations is the substring of s2.
 

**Example 1:**
```
Input: s1 = "ab", s2 = "eidbaooo"
Output: true
Explanation: s2 contains one permutation of s1 ("ba").
```

**Example 2:**
```
Input: s1 = "ab", s2 = "eidboaoo"
Output: false
``` 

**Constraints:**
```
1 <= s1.length, s2.length <= 10^4
s1 and s2 consist of lowercase English letters.
```

**Tags**
- Revisit

### Solution
```
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        """
            Use sliding window. Get the character counts
            of the current window and the character count
            of s1. If they are the same, then return True. Otherwise, False.
            
            Optimization:
            If you use a constant space hashmap of 26 characters, then the
            comparison time is constant. Also, don't recreate the sliding
            window character count. Just update the character count as the 
            window updates.
        """
        s1_counter = collections.defaultdict(int)
        s2_length = len(s2)
        s1_length = len(s1)
        
        for char in s1:
            s1_counter[char] += 1
        
        prev_index = -1
        current_counter = collections.defaultdict(int)
        
        for i in range(s1_length - 1, s2_length):
            if prev_index is -1:
                for j in range(0, s1_length):
                    current_counter[s2[j]] += 1
            else:
                current_counter[s2[prev_index]] -= 1
                if current_counter[s2[prev_index]] == 0:
                    del current_counter[s2[prev_index]]
                current_counter[s2[i]] += 1
            
            if s1_counter == current_counter:
                return True
            
            prev_index += 1
        
        return False
```
