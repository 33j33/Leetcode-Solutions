## Problem

https://leetcode.com/problems/valid-parentheses

## Solution

Starting with an empty stack, process the expression from left to right. If the character in the expression is an opening parenthesis, push it on the stack as a signal that a corresponding closing symbol needs to appear later. If, on the other hand, a character is a closing parenthesis, pop the stack. As long as it is possible to pop the stack to match every closing parenthesis, the parentheses remain balanced. If at any time there is no opening character on the stack to match a closing character, the expression is not balanced properly. At the end of the expression, when all characters have been processed, the stack should be empty.

In addition to above Algo, we call a helper function, matches, to assist with symbol-matching. Each symbol that is removed from the stack must be checked to see that it matches the current closing symbol. If a mismatch occurs, the boolean variable balanced is set to False.

- **Time Complexity** - `O(n)`
- **Space Complexity** - `O(n)`

```python
from collections import deque
class Solution:
    def isValid(self, s: str) -> bool:
        stack = deque()
        
        for char in s:
            if char in "([{":
                stack.append(char)
            if char in ")]}":
                if len(stack) == 0:
                    return False
                else:
                    open_char = stack.pop()
                    if not self.matches(open_char, char):
                        return False
        
        return len(stack) == 0
        
    def matches(self, open_char: str, close_char: str) -> bool:
        opens = "([{"
        closurs = ")]}"
        
        return opens.find(open_char) == closurs.find(close_char)
```