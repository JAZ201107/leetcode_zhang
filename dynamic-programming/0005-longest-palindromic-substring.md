# 0005 Longest Palindromic Substring

[Question](https://leetcode.com/problems/longest-palindromic-substring/description/)

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public String longestPalindrome(String s) {
        int n = s.length();
        int start = 0;
        int end = 0;
        boolean[][] dp = new boolean[n][n];
        for(int len = 0;len<n;len++){
            for(int i =0; i+len<n; i++){
                dp[i][i+len] = s.charAt(i) == s.charAt(i+len) 
                                && (len < 2 || dp[i+1][i+len-1]);
                if(dp[i][i+len]
                && len > end-start){
                    start = i;
                    end = i + len;
                }
            }
        }


        return s.substring(start,end+1);
    }
}
```