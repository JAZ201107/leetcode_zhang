[Question](https://leetcode.com/problems/group-anagrams/)

<img src="0049 Group Anagrams/image-20221013211828985.png">



My Solution:

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        if (strs == null || strs.length == 0)
            return new ArrayList<>();
        
        Map<String, List<String>> map = new HashMap<>();
        for( String s: strs){
            char[] ca = s.toCharArray();
            Arrays.sort(ca); // sort string array
            String keyStr = String.valueOf(ca); // char array to String
            if(!map.containsKey(keyStr))
                map.put(keyStr, new ArrayList<>()); // if not contain, create new arryalist
            map.get(keyStr).add(s);
        }
        
        return new ArrayList<>(map.values());
    }
}
```

