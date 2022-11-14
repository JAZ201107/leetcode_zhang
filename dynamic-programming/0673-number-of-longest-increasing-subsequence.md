# 0673 Number of Longest Increasing Subsequence

[Question](https://leetcode.com/problems/number-of-longest-increasing-subsequence/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int findNumberOfLIS(int[] nums) {
        int len = nums.length;
        int dp[] = new int[len];
        int count[] = new int[len];

        dp[0] = 1;
        count[0] = 1;
        int res = 0;
        int max = Integer.MIN_VALUE;

        for(int i = 1; i < nums.length; i++){
            dp[i] = 1;
            count[i] = 1;
            for(int j = i -1; j >= 0; j--){
                if(nums[j] < nums[i]){
                    if(dp[i] < dp[j] + 1){
                        dp[i] = dp[j] + 1;
                        count[i] = count[j];
                    }else if(dp[i] == dp[j] + 1){
                        count[i] += count[j];
                    }
                }
            }
        }

        for(int i = 0; i < nums.length; i++){
            if(max < dp[i]){
                res = count[i];
                max = dp[i];
            }else if(max == dp[i]){
                res += count[i];
            }
        }


        return res;
    }
}
```
