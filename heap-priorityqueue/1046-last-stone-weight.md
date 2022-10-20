# 1046 Last Stone Weight

[Question](https://leetcode.com/problems/last-stone-weight/)

![](<../.gitbook/assets/image (6) (1).png>)

My Solution

```java
class Solution {
    public int lastStoneWeight(int[] stones) {
        PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());
        for(int st: stones) {
            pq.add(st);
        }
        
        while(pq.size() > 1) {
            int x = pq.poll();
            int y = pq.poll();
            if(x > y) {
                pq.add(x - y);
            }
        }
        return pq.isEmpty() ? 0 : pq.peek();
    }
}
```
