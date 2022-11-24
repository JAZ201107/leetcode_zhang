# 0409 Longest Palindrome

[Question](https://leetcode.com/problems/longest-palindrome/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int longestPalindrome(String s) {
        int length = 0;
        Set<Character> set = new HashSet<>();

        for(int i=0; i<s.length(); i++){
            char c = s.charAt(i);
            if(set.contains(c)){
                length += 2;
                set.remove(c);
            }else{
                set.add(c);
            }
        }

        // odd 
        if(set.size() > 0){
            length++;
        }

        return length;
    }
}
```