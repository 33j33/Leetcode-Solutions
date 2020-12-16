## Problem

https://leetcode.com/problems/reverse-integer/

## Solution

```python
class Solution:
    def reverse(self, x: int) -> int:
        
        num = abs(x)
        revNum = 0
        while(num > 0):
            rem = num % 10
            revNum = revNum * 10 + rem
            num = num // 10
            
        # Check for overflow
        if (x <= -2**31 or x >= 2**31-1):
            return 0
        # Check for overflow
        if (revNum <= -2**31 or revNum >= 2**31-1):
            return 0
        if x < 0:
            return -revNum
        else:
            return revNum
```