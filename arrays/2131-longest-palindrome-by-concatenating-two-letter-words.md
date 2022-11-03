# 2131 Longest Palindrome by Concatenating Two Letter Words

[Question](https://leetcode.com/problems/longest-palindrome-by-concatenating-two-letter-words/)

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

My Solution:

```java
class Solution {
    public int longestPalindrome(String[] words) {
        int counter[][] = new int[26][26];
        int ans = 0;
        for(String w: words){
            int a = w.charAt(0) - 'a';
            int b = w.charAt(1) - 'a';
            
            if(counter[b][a] > 0){
                ans += 4;
                counter[b][a]--;
            }else {
                counter[a][b]++;
            }
        }
        
        
        for(int i = 0; i< 26; i++){
            if(counter[i][i] > 0){
                ans += 2;
                break;
            }
        }
        
        
        return ans;
    }
}
```
