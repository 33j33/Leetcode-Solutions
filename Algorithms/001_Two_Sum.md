## Problem

https://leetcode.com/problems/two-sum

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

 

Example 1:

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].
```


## Solution

**Bruteforce** Solution would be Loop through each element `x` and find if there is another value that equals to `target − x`. We would need two `for` loops for this. And it would require `O(n^2)` time complexity.

**Optimised Solution** 

To improve our run time complexity, we need a more efficient way to check if the complement exists in the array. If the complement exists, we need to look up its index. What is the best way to maintain a mapping of each element in the array to its index? A hash table.

We reduce the look up time from `O(n)` to `O(1)` by trading space for speed. A hash table is built exactly for this purpose, it supports fast look up in near constant time. I say "near" because if a collision occurred, a look up could degenerate to `O(n)` time. But look up in hash table should be amortized `O(1)` time as long as the hash function was chosen carefully. 

Complexity - 

- Time complexity : `O(n)`. We traverse the list containing nnn elements only once. Each look up in the table costs only `O(1)` time.

- Space complexity : `O(n)`. The extra space required depends on the number of items stored in the hash table, which stores at most `n` elements.

While we iterate and inserting elements into the table, we also look back to check if current element's complement already exists in the table. If it exists, we have found a solution and return immediately.


```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        # Check for compliment in hashMap for each number
        # if it exists then return the indices (you got the answer)
        # else insert the number in the hashtable/hashmap
        hashMap = dict()
        for i, num in enumerate(nums):
            compliment = target - num
            
            if compliment not in hashMap:
                hashMap[num] = i
            else:
                return [hashMap[compliment], i]
```


