# 0647 Palindromic Substrings

Question

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int countSubstrings(String s) {
        char[] sArray = s.toCharArray();
        int s_len = sArray.length;
        if(s_len == 1){
            return 1;
        }
        int count = 0;
        boolean[][] dp = new boolean[s_len][2];
        int currCol = 0;

        for(int len = 0; len < s_len; len++){
            for(int start = 0; start + len < s_len; start++){
                int end = start + len;
                if(len == 0){
                    dp[start][currCol] = true;
                    count++;
                }else if(len == 1){
                    if(sArray[start] == sArray[end]){
                        dp[start][currCol] = true;
                        count++;
                    }else{
                        dp[start][currCol] = false;
                    }
                }else{
                    if(sArray[start] == sArray[end] && dp[start+1][currCol]){
                        dp[start][currCol] = true;
                        count++;
                    }else{
                        dp[start][currCol] = false;
                    }
                }
            }
            currCol = 1 - currCol;
        }// end for
        return count;
    }
}
```
