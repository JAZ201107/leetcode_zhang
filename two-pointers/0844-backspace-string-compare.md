# 0844 Backspace String Compare

[Question](https://leetcode.com/problems/backspace-string-compare/)

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>



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



My Solution 2: Two Pointer

```java
class Solution {
    public boolean backspaceCompare(String s, String t) {
        int i = s.length() - 1;
        int j = t.length() - 1;
        int countIns = 0;
        int countInt = 0;
        
        while(true){
            while(i >= 0){
                if(s.charAt(i) == '#'){
                    countIns++;
                    i--;
                }else if(countIns > 0){
                    countIns--;
                    i--;
                }else{
                    break;
                }
            }// end while()
            
            while(j >= 0){
                if(t.charAt(j) == '#'){
                    countInt++;
                    j--;
                }else if(countInt > 0){
                    countInt--;
                    j--;
                }else{
                    break;
                }
            }
            
            if(i >= 0
              && j >= 0){
                if(s.charAt(i) == t.charAt(j)){
                    i--;
                    j--;
                }else{
                    return false;
                }
            }else{
                break;
            }
        }// end while()
        
        
        return i == j;
    }
}
```
