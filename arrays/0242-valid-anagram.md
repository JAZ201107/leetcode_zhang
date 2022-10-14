# 0242 Valid Anagram

[Question](https://leetcode.com/problems/valid-anagram/)

![](../.gitbook/assets/image-20221013210135348.png)

My Solution:

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        int[] arr = new int[26];
        if(s.length() != t.length() ) return false;
        for (int i = 0; i < s.length(); i++) {
            arr[s.charAt(i) - 'a']++;
        }
        for (int i = 0; i < t.length(); i++) {
            if(--arr[t.charAt(i)-'a'] < 0) {
                return false;
            }
        }
        return true;
    }
}
```
