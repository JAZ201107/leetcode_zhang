# 1832 Check if the Sentence Is Pangram

[Question](https://leetcode.com/problems/check-if-the-sentence-is-pangram/)

![](<../.gitbook/assets/image (4) (2).png>)



My solution:

```java
class Solution {
    public boolean checkIfPangram(String sentence) {
        if(sentence.length() < 26){
            return false;
        }       
        
        int[] appear = new int[26];
        char[] string_s = sentence.toCharArray();
        int count = 0;
        for(char i: string_s){
            int i_p = i - 'a';
            if(appear[i_p] == 1){
                continue;
            }else{
                appear[i_p] = 1;
                count++;
            }
        }
        
        return count == 26;
    }
}
```



Solution2:

```java
class Solution {
    public boolean checkIfPangram(String sentence) {
        for(int i=0;i<26;i++){
            int c=(char)('a'+i);
            if(sentence.indexOf(c)==-1){
                return false;
            }
        }return true;
    }
}
```
