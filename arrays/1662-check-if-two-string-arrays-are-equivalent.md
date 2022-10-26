# 1662 Check If Two String Arrays are Equivalent

[Question](https://leetcode.com/problems/check-if-two-string-arrays-are-equivalent/)

<figure><img src="../.gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>



My Solution: StringBuilder()

```java
class Solution {
    public boolean arrayStringsAreEqual(String[] word1, String[] word2) {
        StringBuilder s1 = new StringBuilder();
        StringBuilder s2 = new StringBuilder();
        
        for(String s : word1){
            s1.append(s);
        }
        
        for(String s: word2){
            s2.append(s);
        }
        
        return s1.toString().equals(s2.toString());
    }
}
```



My Solution: String.join()

```java
class Solution {
    public boolean arrayStringsAreEqual(String[] word1, String[] word2) {
        return(String.join("", word1).equals(String.join("", word2)));
    }
}
```
