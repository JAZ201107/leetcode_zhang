# 2284 Sender With Largest Word Count

[Question](https://leetcode.com/problems/sender-with-largest-word-count/)

![](<../.gitbook/assets/image (8) (1) (1) (1).png>)

My Solution:

```java
class Solution {
    public String largestWordCount(String[] messages, String[] senders) {
        Map<String, Integer> freq = new HashMap<>();
        for(int i = 0; i < messages.length; i++){
            freq.put(
                senders[i], freq.getOrDefault(senders[i], 0) + count(messages[i])
                    );
        }
        
        List<String> res = new ArrayList(freq.keySet());
        
        // sorting
        Collections.sort(res, (u1, u2)->freq.get(u1).equals(freq.get(u2))?
                        -u1.compareTo(u2): freq.get(u2) - freq.get(u1)
                        );
        
        return res.get(0);
    }
    
    private int count(String s){
        return s.split("\\s+").length;
    }
}
```



My Solution2:

```java
class Solution {
    public String largestWordCount(String[] messages, String[] senders) {
        Map<String, Integer> freq = new HashMap<>();
        int max = 0;
        String name = "";
        for(int i = 0; i < messages.length; i++){
            freq.put(
                senders[i], freq.getOrDefault(senders[i], 0) + count(messages[i])
                    );
            
            if( freq.get(senders[i]) > max ){
                max  = freq.get(senders[i]);
                name = senders[i];
            }else if(freq.get(senders[i]) == freq.get(name) && name.compareTo(senders[i]) < 0){
                name = senders[i];
            }
        }
        
        
        return name;
    }
    
    private int count(String s){
        return s.split("\\s+").length;
    }
}
```
