### 76. Minimum Window Substring

Given a string `S` and a string `T`, find the minimum window in `S` which will contain all the characters in `T` in complexity `O(n)`.

**Example:**
```
Input: S = "ADOBECODEBANC", T = "ABC"
Output: "BANC"
```
**Note:**
- If there is no such window in `S` that covers all characters in `T`, return the empty string `""`.
- If there is such window, you are guaranteed that there will always be only one unique minimum window in `S`.

### Solution
```
/**
 * @param {string} s
 * @param {string} t
 * @return {string}
 */
var minWindow = function(s, t) {
    let slowPtr = 0;
    let fastPtr = 0;
    let result = [];
    // store counts by letter here
    let map = {};
    // store the total char count here
    let count = 0;
    // store lettersNeeded here
    let lettersNeeded = {};
    const length = t.length;
    
    if (!t.length || !s.length) {
        return '';
    }
    
    for (let i = 0; i < t.length; i++) {
        lettersNeeded[t[i]] = lettersNeeded[t[i]] || 0;
        lettersNeeded[t[i]] += 1;
    }
    
    while (fastPtr < s.length) {
        let fastPtrChar = s[fastPtr];
        // not a char we care about: skip it
        if (t.indexOf(fastPtrChar) < 0) {
            fastPtr += 1;
            continue;
        }
        
        map[fastPtrChar] = map[fastPtrChar] || 0;
        // first time? increment count
        if (map[fastPtrChar] < lettersNeeded[fastPtrChar]) {
            count += 1;
        }
        map[fastPtrChar] += 1;
        
        // did not find all chars yet: continue fastPtr
        if (count !== length) {
            fastPtr += 1;
            continue;
        }
        
        // slowly decrement slowPtr while checking for min
        while (slowPtr <= fastPtr) {
            let newLength = fastPtr - slowPtr + 1;
            if (!result.length) {
                result = [slowPtr, fastPtr];
            }
            // find the min interval
            let currLength = result[1] - result[0] + 1;
            if (newLength < currLength) {
                result = [slowPtr, fastPtr];
            }
            let slowPtrChar = s[slowPtr];
            // if slowPtrChar is not what we care about: move it and skip it
            if (map[slowPtrChar] === undefined) {
                slowPtr += 1;
                continue;
            }
            // decrement count and move slowPtr
            map[slowPtrChar] -= 1;
            slowPtr += 1;
            
            // decrement total count if the char goes down to zero
            if (map[slowPtrChar] < lettersNeeded[slowPtrChar]) {
                count -= 1;
            }
            // this means we need to keep searching with fastPtr
            if (count < length) {
                fastPtr += 1;
                break;
            }
        }
    }
    
    if (!result.length) {
        return '';
    }
    
    return s.substring(result[0], result[1] + 1);
};
```