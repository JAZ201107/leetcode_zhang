# 0021 Merge Two Sorted Lists

Question

<figure><img src="../.gitbook/assets/image (1) (13).png" alt=""><figcaption></figcaption></figure>



My Solution:

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode()
        tail = dummy # point to the current node

        # while both list1 and list2 are not empty
        while list1 and list2:
            if list1.val < list2.val:
                tail.next = list1
                list1 = list1.next
            else:
                tail.next = list2
                list2 = list2.next
            tail = tail.next # update pointer
        
        if list1:
            tail.next = list1
        elif list2:
            tail.next = list2
        
        return dummy.next
```
