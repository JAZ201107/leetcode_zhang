# 0082 Remove Duplicates from Sorted List II

[Question](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>



My Solution 1:

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
        if(head == null || head.next == null){
            return head;
        }

        ListNode dumm = new ListNode(0, head);
        ListNode curr = dumm;

        while(head != null){
            if( head.next != null
                && head.val == head.next.val){
                while(head.next != null && head.val == head.next.val){
                    head = head.next;
                }
                curr.next = head.next;
            }else{
                curr = curr.next;
            }
            head = head.next;
        }

        return dumm.next;
    }
}
```

My Solution 2:

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
        if(head == null 
          || head.next == null){
            return head;
        }
        ListNode res = new ListNode(0);
        ListNode slow = res;
        ListNode fast = head;
        
        slow.next = fast;
        
        while(fast != null){
            
            while(fast.next != null
                 && fast.val == fast.next.val){
                fast = fast.next;
            }
            
            if(slow.next != fast){
                slow.next = fast.next;
                fast = slow.next;
            }else {
                slow = slow.next;
                fast = fast.next;
            }
        }
        
        return res.next;
        
    }
}
```
