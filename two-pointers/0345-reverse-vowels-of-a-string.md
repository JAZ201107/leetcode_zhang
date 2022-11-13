# 0345 Reverse Vowels of a String

[Question](https://leetcode.com/problems/reverse-vowels-of-a-string/description/)

<figure><img src="../.gitbook/assets/image (1) (1) (7).png" alt=""><figcaption></figcaption></figure>

My Solution:

```java
class Solution {
    public String reverseVowels(String s) {
        List<Character> list = Arrays.asList('a','e','i','o','u','A','E','I','O','U');

        char[] ch = s.toCharArray();

        int begin = 0;
        int end = ch.length - 1;

        while(begin < end){
            if(list.contains(ch[begin])
            && list.contains(ch[end])){
                char temp = ch[begin];
                ch[begin] = ch[end];
                ch[end] = temp;
                begin++;
                end--;
            }else if(list.contains(ch[begin])
            && !list.contains(ch[end])){
                end--;
            }else if(!list.contains(ch[begin])
            && list.contains(ch[end])){
                begin++;
            }else if(!list.contains(ch[begin])
            && !list.contains(ch[end])){
                end--;
                begin++;
            }
        }

        return String.valueOf(ch);
    }
}
```
