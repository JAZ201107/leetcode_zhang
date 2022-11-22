# 0706 Design HashMap

[Question](https://leetcode.com/problems/design-hashmap/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (1) (4).png" alt=""><figcaption></figcaption></figure>



My Solution 1: Array

```java
class MyHashMap {

    int size = (int)Math.pow(10,6) + 1;
    int[] flag;

    public MyHashMap() {
        flag = new int[size];
    }
    
    public void put(int key, int value) {
        // flag initial with 0, so, store 0 as 1, 1 as 2....
        flag[key] = value + 1;
    }
    
    public int get(int key) {
        if(flag[key] == 0){
            return -1;
        }else {
            return flag[key] - 1;
        }
    }
    
    public void remove(int key) {
        flag[key] = 0;
    }
}

/**
 * Your MyHashMap object will be instantiated and called as such:
 * MyHashMap obj = new MyHashMap();
 * obj.put(key,value);
 * int param_2 = obj.get(key);
 * obj.remove(key);
 */
```



My Solution 2: List & Array

```java
class MyHashMap {

    private static class ListNode{
        int key, value;
        ListNode next;
        ListNode(int key, int value, ListNode next){
            this.key = key;
            this.value = value;
            this.next = next;
        }
    }

    ListNode[] map;

    private ListNode find(ListNode x, int key){
        if(x == null){
            return null;
        }
        if(x.key == key){
            return x;
        }
        return find(x.next, key);
    }

    private ListNode remove(ListNode x, int key){
        if(x == null){
            return null;
        }
        if(x.key == key){
            return x.next;
        }
        x.next = remove(x.next, key);
        return x;
    }

    public MyHashMap() {
        map = new ListNode[1000000];
    }
    
    public void put(int key, int value) {
        int hash = key % 1000000;
        ListNode x = find(map[hash], key);
        if(x != null){
            x.value = value;
        }else{
            map[hash] = new ListNode(key, value, map[hash]);
        }
    }
    
    public int get(int key) {
        int hash = key % 1000000;
        ListNode x = find(map[hash], key);
        if(x != null){
            return x.value;
        }
        return -1;
    }
    
    public void remove(int key) {
        int hash = key % 1000000;
        map[hash] = remove(map[hash], key);
    }
}

/**
 * Your MyHashMap object will be instantiated and called as such:
 * MyHashMap obj = new MyHashMap();
 * obj.put(key,value);
 * int param_2 = obj.get(key);
 * obj.remove(key);
 */
```
