### 224. Basic Calculator

Implement a basic calculator to evaluate a simple expression string.

The expression string may contain open ( and closing parentheses ), the plus + or minus sign -, non-negative integers and empty spaces .

**Example 1:**
```
Input: "1 + 1"
Output: 2
```

**Example 2:**
```
Input: " 2-1 + 2 "
Output: 3
```

**Example 3:**
```
Input: "(1+(4+5+2)-3)+(6+8)"
Output: 23
Note:
You may assume that the given expression is always valid.
Do not use the eval built-in library function.
```

### Solution:
- Use a stack
- there is a case that you need to account for.
```
/**
 * @param {string} s
 * @return {number}
 */
var calculate = function(s) {
    let stack = [];
    let compute = (arr) => {
        let operation = '+';
        let ans = 0;
        let num = 0;
        for (let i = 0; i < arr.length; i++) {
            let char = arr[i];
            if (char === '(' || char === ')') {
                continue;
            }
            if (char === '+' || char === '-') {
                ans = operation === '+' ? ans + num : ans - num;
                num = 0;
                operation = char;
            } else {
                char = parseInt(char);
                num = num * 10 + char;
            }
        }
        ans = operation === '+' ? ans + num : ans - num;
        return ans;
    }
    
    for (let i = 0; i < s.length; i++) {
        let char = s[i];
        if (char === ' ') {
            continue;
        }
        if (char === ')') {
            let open = stack.lastIndexOf('(');
            let expr = stack.splice(open);
            stack.push(compute(expr));
            continue;
        }
        
        stack.push(char);
    }
    return compute(stack);
};
```
