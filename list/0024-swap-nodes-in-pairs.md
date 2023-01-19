# 0024 Swap Nodes in Pairs

[Question](https://leetcode.com/problems/swap-nodes-in-pairs/description/)

<figure><img src="../.gitbook/assets/image (4) (10).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>

## JAVA

My Solution:

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode swapPairs(ListNode head) {
        ListNode dummy = new ListNode(0, head);
        ListNode prev = dummy;
        ListNode curr = head;

        while(curr != null
        && curr.next != null){
            ListNode nextPair = curr.next.next;
            ListNode second = curr.next;

            // reserver this pair(curr, second)
            second.next = curr;
            curr.next = nextPair;
            prev.next = second;

            // update pairs
            prev = curr;
            curr = nextPair;
        }

        return dummy.next;
    }
}
```



## Python

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode(0, head)
        prev, curr = dummy, head

        while curr and curr.next:
            nextPair = curr.next.next
            second = curr.next

            # reverse
            prev.next = second
            second.next = curr
            curr.next = nextPair

            # update
            prev = curr
            curr = nextPair

        return dummy.next
```
