# 0083 Remove Duplicates from Sorted List

[Question](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)

<figure><img src="../.gitbook/assets/image (4) (9).png" alt=""><figcaption></figcaption></figure>



&#x20;My Solution:

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
    public ListNode deleteDuplicates(ListNode head) {
        if(head==null) return head;
        // ListNode tmp = head;
        ListNode tmp = head;
        while(tmp.next != null)
        {
            if(tmp.val == tmp.next.val)
            {
                tmp.next = tmp.next.next;
            }else
            {
                tmp = tmp.next;
            }
        }
        return head;
    }
}
```
