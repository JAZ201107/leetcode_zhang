# 0706 Design HashMap

[Question](https://leetcode.com/problems/design-hashmap/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



My Solution:

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
