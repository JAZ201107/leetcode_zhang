# 0409 Longest Palindrome

[Question](https://leetcode.com/problems/longest-palindrome/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (4) (8) (1).png" alt=""><figcaption></figcaption></figure>



My Solution 1: HashSet

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





My Solution 2: Array

```java
class Solution {
    public int longestPalindrome(String s) {
        int[] count = new int[128];
        for(char c: s.toCharArray()){
            count[c]++;
        }

        int len = 0;
        for(int i: count){
            len += 2*(i/2);
        }

        return len < s.length() ? len + 1:len;
    }
}
```
