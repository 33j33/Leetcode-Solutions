## Problem

https://leetcode.com/problems/longest-common-prefix

## Solution

[Watch the video for explaination] https://www.youtube.com/watch?v=bl8ue-dTxgs 

```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        # In the this approach we traverse
        # over each string in the array simultaneously
        
        if not strs:
            return ""
        
        # shortest string
        shortest = min(strs,key=len)
        
        for i, ch in enumerate(shortest):
            for otherStr in strs:
                if otherStr[i] != ch:
                    return shortest[:i]
        return shortest 
```
- **Time Complexity** - `O(n*m)` where `n` is the length of array and `m` is the length of shortest string
- **Space Complexity** - `O(1)` 

#### Other approaches to solving the problem

https://www.geeksforgeeks.org/longest-common-prefix-using-word-by-word-matching/