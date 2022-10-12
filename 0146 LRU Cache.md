[Question](https://leetcode.com/problems/lru-cache/)

<img src="0146 LRU Cache/image-20221012194331449.png">



My Soltuion:

```java
class LRUCache {
    // Linked Nodes
    private class Node{
        int key, value;
        Node prev, next;
        Node(int k, int v){
            this.key = k;
            this.value = v;
        }
        Node(){
            this(0,0);
        }
    }
    
    private final int CAPACITY;
    private int count;
    private Map<Integer, Node> map;
    private Node head, tail;
    
    public LRUCache(int capacity) {
        this.CAPACITY = capacity;
        this.count = 0;
        map = new HashMap<>();
        head = new Node();
        tail = new Node();
        head.next = tail;
        tail.prev = head;
    }
    
    public int get(int key) {
        Node n = map.get(key);
        if(n == null){
            return -1;
        }
        update(n); // key has been used
        return n.value;
    }
    
    private void update(Node node){
        remove(node);
        add(node);
    }
    
    private void add(Node node){
        Node after = head.next;
        head.next = node;
        node.prev = head;
        node.next = after;
        after.prev = node;
    }
    
    private void remove(Node node){
        Node before = node.prev, after = node.next;
        before.next = after;
        after.prev = before;
    }
    
    public void put(int key, int value) {
        Node n = map.get(key);
        if(n == null){
            n = new Node(key, value);
            map.put(key, n);
            add(n);
            count++;
        }else{
            n.value = value;
            update(n);
        }
        
        if(this.count > this.CAPACITY){
            Node toDel = tail.prev;
            remove(toDel);
            map.remove(toDel.key);
            count--;
        }
    }
}
```

