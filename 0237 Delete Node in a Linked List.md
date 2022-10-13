[Question](https://leetcode.com/problems/delete-node-in-a-linked-list/)

<img src="0237 Delete Node in a Linked List/image-20221013115853045.png">



My Solution:

```java
class Solution {
    public void deleteNode(ListNode node) {
        if(node ! = null && node.next ! = null){
            node.val = node.next.val;
            node.next = node.next.next;
        }
    }
}
```

