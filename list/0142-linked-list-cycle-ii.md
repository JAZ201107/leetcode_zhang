# 0142 Linked List Cycle II

[Question](https://leetcode.com/problems/linked-list-cycle-ii/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>



## JAVA

My Solution:&#x20;

```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    private ListNode intersection(ListNode head){
        ListNode slow = head;
        ListNode fast = head;

        while(fast != null && fast.next != null){
            slow = slow.next;
            fast = fast.next.next;

            if(slow == fast){
                return slow;
            }
        }

        return null;
    }
    public ListNode detectCycle(ListNode head) {
        if(head == null || head.next == null){
            return null;
        }

        // Node that slow and fast meet
        ListNode intersect = intersection(head);
        if(intersect == null){
            return null; // no circle
        }

        ListNode  start = head;
        while(intersect != start){
            start = start.next;
            intersect = intersect.next;
        }

        return start;
    }
}
```



## Python

My Solution:

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        if(head is None  or head.next is None):
            return None

        
        intersect = self.intersection(head)
        if(intersect is None):
            return None
        
        start = head
        while(start != intersect):
            start = start.next
            intersect = intersect.next 

        return start

        

    def intersection(self, head: Optional[ListNode]) -> Optional[ListNode]:
        slow = head
        fast = head


        while(fast is not None and fast.next is not None):
            slow = slow.next
            fast = fast.next.next

            if(slow == fast):
                return slow

        return None
```
