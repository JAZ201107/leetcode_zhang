# 0300 Longest Increasing Subsequence

[Question](https://leetcode.com/problems/longest-increasing-subsequence/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        int[] dp = new int[nums.length];
        int max = 1;

        for(int i = 0; i < nums.length; i++){
            dp[i] = 1;
            for(int j = 0; j < i; j++){
                if(nums[j] < nums[i]){
                    dp[i] = Math.max(dp[i], dp[j] +1);
                    max = Math.max(dp[i], max);
                }
            }
        }

        return max;
    }
}
```
