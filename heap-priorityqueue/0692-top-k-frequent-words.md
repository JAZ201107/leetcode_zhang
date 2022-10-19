# 0692 Top K Frequent Words

[Question](https://leetcode.com/problems/top-k-frequent-words/)

![](<../.gitbook/assets/image (2).png>)



My Solution:

```java
class Solution {
    public List<String> topKFrequent(String[] words, int k) {
        // count frequence
        HashMap<String, Integer> freq = new HashMap<>();
        for(int i = 0; i<words.length;i++){
            freq.put(words[i], freq.getOrDefault(words[i], 0)+1);
        }
        
        List<String> res = new ArrayList(freq.keySet());
        
        // sorting
        Collections.sort(res, (w1, w2) -> freq.get(w1).equals(freq.get(w2)) ?
                        w1.compareTo(w2): freq.get(w2) - freq.get(w1));
        
        return res.subList(0,k);
    }
}
```



My Solution2:

```java
class Solution {
    public List<String> topKFrequent(String[] words, int k) {
        // count frequence
        HashMap<String, Integer> freq = new HashMap<>();
        for(int i = 0; i<words.length;i++){
            freq.put(words[i], freq.getOrDefault(words[i], 0)+1);
        }
        
        PriorityQueue<Map.Entry<String, Integer>> pq = new PriorityQueue<>(
            (a,b) -> (
                a.getValue() == b.getValue() ? a.getKey().compareTo(b.getKey())
                : (a.getValue() - b.getValue())*(-1)
            )
        );
        
        for(Map.Entry<String, Integer> e: freq.entrySet()){
            pq.offer(e);
        }
        
        List<String> result = new ArrayList<>();
        while(k > 0){
            k--;
            result.add(pq.poll().getKey());
        }
        
        return result;
    }
}
```
