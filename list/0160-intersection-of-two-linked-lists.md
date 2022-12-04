# 0160 Intersection of Two Linked Lists

[Question](https://leetcode.com/problems/intersection-of-two-linked-lists/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (1) (2) (4).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

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



My Solution 2: Compare Nodes

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
        ListNode pointerA = headA;
        ListNode pointerB = headB;

        int lenA = getLen(headA);
        int lenB = getLen(headB);

        if(lenA > lenB){
            for(int i = 0; i < lenA - lenB; i++){
                pointerA = pointerA.next;
            }
        }else if(lenA < lenB){
            for(int i = 0; i < lenB - lenA; i++){
                pointerB = pointerB.next;
            }
        }


        while(pointerA != null){
            if(pointerA == pointerB){
                return pointerA;
            }
            pointerA = pointerA.next;
            pointerB = pointerB.next;
        }

        return null;
    }

    private int getLen(ListNode list){
        int res = 0;
        ListNode pointer = list;
        while(pointer != null){
            res++;
            pointer = pointer.next;
        }

        return res;
    }
}
```



&#x20;My Solution 3:

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
        ListNode pointerA = headA;
        ListNode pointerB = headB;

        while(pointerA != pointerB){
            pointerA = pointerA == null ? headB : pointerA.next;
            pointerB = pointerB == null ? headA : pointerB.next;
        }

        return pointerA;
    }
}
```
