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





## Python

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        def alphanum(c):
            return (
                ord("A") <= ord(c) <= ord("Z") or
                ord("a") <= ord(c) <= ord("z") or
                ord("0") <= ord(c) <= ord("9")
             )
        
        l, r = 0, len(s) - 1
        while l < r:
            while l < r and not alphanum(s[l]):
                l += 1
            while l < r and not alphanum(s[r]):
                r -= 1
            if s[l].lower() != s[r].lower():
                return False
            l += 1
            r -= 1
        return True
```

