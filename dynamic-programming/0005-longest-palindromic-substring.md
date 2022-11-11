# 0005 Longest Palindromic Substring

[Question](https://leetcode.com/problems/longest-palindromic-substring/description/)

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public String longestPalindrome(String s) {
        int len = s.length();
        int start = 0;
        int end = 0;

        boolean[][] dp = new boolean[len][len];
        for(int i = 0; i < len; i++){
            for(int j = 0; i+j < len; j++){
                dp[j][i+j] = s.charAt(j) == s.charAt(j+i)
                            && (i < 2 || dp[j+1][i+j - 1]);
                            
                if(dp[j][j+i]
                    && i > end - start){
                    start = j;
                    end = j + i;
                }
            }
        }

        return s.substring(start, end + 1);
    }
}
```
