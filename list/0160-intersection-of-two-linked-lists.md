# 0160 Intersection of Two Linked Lists

[Question](https://leetcode.com/problems/intersection-of-two-linked-lists/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



My Solution 1: HashSet

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        Set<ListNode> set = new HashSet<>();

        while(headA != null){
            set.add(headA);
            headA = headA.next;
        }

        while(headB != null){
            if(!set.add(headB)){
                return headB;
            }else{
                headB = headB.next;
            }
        }

        return null;
    }
}
```

