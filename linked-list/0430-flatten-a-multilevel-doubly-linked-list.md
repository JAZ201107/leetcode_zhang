# 0430 Flatten a Multilevel Doubly Linked List

[Question](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/)

![](<../.gitbook/assets/image (3).png>)



```java
/*
// Definition for a Node.
class Node {
    public int val;
    public Node prev;
    public Node next;
    public Node child;
};
*/

class Solution {
    public Node flatten(Node head) {
        Node pointer = head;
        while(pointer != null){
            if(pointer.child != null){
                Node tail = helper(pointer.child);
                if(pointer.next != null){
                    pointer.next.prev = tail;
                }
                
                tail.next = pointer.next;
                pointer.next = pointer.child;
                pointer.next.prev = pointer;
                pointer.child = null;
            }
            
            pointer = pointer.next;
        }
        
        return head;
    }
    
    
    private Node helper(Node n){
        while(n.next != null){
            n = n.next;
        }
        return n;
    }
}
```
