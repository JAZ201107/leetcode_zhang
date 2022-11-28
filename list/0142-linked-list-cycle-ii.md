# 0142 Linked List Cycle II

[Question](https://leetcode.com/problems/linked-list-cycle-ii/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



My Solution:

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
