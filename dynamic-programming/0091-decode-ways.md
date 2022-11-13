# 0091 Decode Ways

[Question](https://leetcode.com/problems/decode-ways/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int numDecodings(String s) {
        int len = s.length();
        int[] dp = new int[len+1];
        dp[0] = 1;

        if(s.charAt(0) != '0'){
            dp[1] = 1;
        }

        for(int i = 2; i < len+1; i++){
            if(s.charAt(i-1) != '0'){
                dp[i] += dp[i-1];
            }
            int val = Integer.valueOf(s.substring(i-2, i));
            if(val >= 10 
                && val <= 26){
                    dp[i] += dp[i-2];
            }
        }

        return dp[len];
    }
}
```
