## Problem

https://leetcode.com/problems/roman-to-integer/

## Solution

- **Time Complexity** - `O(n)`
- **Space Complexity** - `O(r)` where r is the number of roman symbols.

```python
class Solution:
    def romanToInt(self, s):
        roman = {'M': 1000,'D': 500 ,'C': 100,'L': 50,'X': 10,'V': 5,'I': 1}
        result = 0
        for i in range(0, len(s) - 1):
            if roman[s[i]] < roman[s[i+1]]:
                result -= roman[s[i]] 
            else:
                result += roman[s[i]]
        return result + roman[s[-1]]

# Note: The trick is that the last letter is always added. Except the last one, if one letter is less than its latter one, this letter is subtracted.
```