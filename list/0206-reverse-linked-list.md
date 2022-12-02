# 0206 Reverse Linked List

[Question](https://leetcode.com/problems/reverse-linked-list/description/)

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>





## Python&#x20;

My Solution 1: Two pointer

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        prev, curr = None, head

        while curr:
            nxt = curr.next # save the next node
            curr.next = prev
            prev = curr
            curr = nxt
        
        return prev

```



My Solution 2: Recursive

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head:
            return None
        
        newHead = head
        if head.next:
            newHead = self.reverseList(head.next)
            head.next.next = head
        head.next = None

        return newHead
```
