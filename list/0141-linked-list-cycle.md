# 0141 Linked List Cycle

Question

<figure><img src="../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>



My Solution:

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        if head == None:
            return False
        slow, fast = head, head.next
        while fast and fast.next:
            if slow == fast:
                return True
            fast = fast.next.next
            slow = slow.next
        
        return False
```
