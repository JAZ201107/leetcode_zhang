# 0451 Sort Characters By Frequency

[Question](https://leetcode.com/problems/sort-characters-by-frequency/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (1) (10).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public String frequencySort(String s) {
        Map<Character,Integer> map = new HashMap();
        for(char c : s.toCharArray()){
            map.put(c, map.getOrDefault(c,0) + 1);
        }

        PriorityQueue<Character> pq = new PriorityQueue((a,b) -> map.get(b) - map.get(a));
        for(char c: map.keySet()){
            pq.offer(c);
        }

        StringBuilder sb = new StringBuilder();
        while(!pq.isEmpty()){
            char c = pq.poll();
            for(int i = 0; i < map.get(c); i++){
                sb.append(c);
            }
        }

        return sb.toString();
    }
}
```
