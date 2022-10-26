# 0125 Valid Palindrome

[Question](https://leetcode.com/problems/valid-palindrome/)

![](<../.gitbook/assets/image (2) (2) (1).png>)



My solution:

```java
class Solution {
    public boolean isPalindrome(String s) {
        int l_p = 0;
        int r_p = s.length() - 1;
        while(r_p > l_p){
            char l_c = s.charAt(l_p);
            char r_c = s.charAt(r_p);
            
            if(!Character.isLetterOrDigit(l_c)){
                l_p++;
            }else if(!Character.isLetterOrDigit(r_c)){
                r_p--;
            }else {
                if(Character.toLowerCase(l_c) != Character.toLowerCase(r_c)){
                    return false;
                }
                
                l_p++;
                r_p--;
            }
        }// end while
        
        return true;
    }
}
```
