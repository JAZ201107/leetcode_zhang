# 0290 Word Pattern

[Question](https://leetcode.com/problems/word-pattern/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public boolean wordPattern(String pattern, String s) {
        String[] words = s.split(" ");
        if (words.length != pattern.length()){
            return false;
        }
        
        Map<Character, String> map1 = new HashMap<>();
        Map<String, Boolean> map2 = new HashMap<>();

        for(int i = 0; i < words.length; i++){
            char ch = pattern.charAt(i);
            if(map1.containsKey(ch) == false){
                if(map2.containsKey(words[i])){
                    return false;
                }else{
                    map1.put(ch, words[i]);
                    map2.put(words[i], true);
                }
            }else{
                String m = map1.get(ch);
                if(!m.equals(words[i])){
                    return false;
                }
            }
        }
        
        return true;
    }
}
```
