# 0844 Backspace String Compare

[Question](https://leetcode.com/problems/backspace-string-compare/)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public boolean backspaceCompare(String s, String t) {
        return sb(s).equals(sb(t));
    }
    
    
    private String sb(String str){
        StringBuilder s = new StringBuilder();
        
        for(char c: str.toCharArray()){
            if(c!='#'){
                s.append(c);
            }else if(s.length() != 0){
                s.deleteCharAt(s.length() - 1);
            }
        }
        
        
        return s.toString();
    }
}
```

