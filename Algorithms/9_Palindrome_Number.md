## Problem

https://leetcode.com/problems/palindrome-number/submissions/

## Solution

```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if (x < 0):
            return False
        revNum = self.reverseNum(x)
        return revNum == x
        
    def reverseNum(self, num: int) -> int:
        
        temp = num
        revNum = 0
        while(temp > 0):
            rem = temp % 10
            revNum = revNum * 10 + rem
            temp = temp // 10
        return revNum
```