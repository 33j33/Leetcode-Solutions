## Problem

https://leetcode.com/problems/merge-two-sorted-lists

## Solution

[Lucid Explanation for iterative and recursive with video] https://leetcode.com/problems/merge-two-sorted-lists/discuss/759870/Python3-Solution-with-a-Detailed-Explanation-dummy-explained

*In-place iterative solution*, takes `O(n+m)` time and `O(1)` space where 
`n` and `m` are length of the lists.

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        # temp is used to traverse and combine l1 and l2
        dummyHead = temp = ListNode(0)
        
        while(l1 and l2):
            if(l1.val < l2.val):
                temp.next = l1
                l1 = l1.next
            else:
                temp.next = l2
                l2 = l2.next
            temp = temp.next
            
        temp.next = l1 or l2
            
        return dummyHead.next
```

