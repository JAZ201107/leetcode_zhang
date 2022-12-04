# 0438 Find All Anagrams in a String

[Question](https://leetcode.com/problems/find-all-anagrams-in-a-string/)

<figure><img src="../.gitbook/assets/image (3) (1) (2) (1).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        List<Integer> res = new LinkedList<>();
        if(s.length()
          < p.length()){
            return res;
        }
        
        // count the number of characters 
        Map<Character, Integer> map = new HashMap<>();
        for(int i=0; i < p.length();i++){
            map.put(p.charAt(i), map.getOrDefault(p.charAt(i), 0) +1);
        }
        
        
        int needMatched = map.size(); // how many character need to be matched
        int start = 0;
        int end = 0;
        
        while(end < s.length()){
            char c = s.charAt(end);
            if(map.containsKey(c)){
                int count = map.get(c);
                if(count == 1){
                    needMatched--;
                }
                map.put(c, count-1);
            }
            end++;
            if(end - start > p.length()){
                char sChar = s.charAt(start);
                if(map.containsKey(sChar)){
                    int count = map.get(sChar);
                    if(count == 0){
                        needMatched++;
                    }
                    map.put(sChar, count+1);
                }
                start++;
            }
            
            if(needMatched == 0){
                res.add(start);
            }
        }
        
        
        return res;
    }
}
```
