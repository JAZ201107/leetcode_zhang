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



My Solution 2:

```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        int len = nums.length;
        int max = 1;

        for(int i = 1; i < len; i++){
            if(nums[i] > nums[max-1]){
                nums[max++] = nums[i];
            }else {
                for(int j = max - 2; ;j--){
                    if(j<0 || nums[i] > nums[j]){
                        nums[j+1] = nums[i];
                        break;
                    }
                }
            }
        }

        return max;
    }
}
```





## Python

```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        DP = [1] * len(nums)

        for i in range(len(nums) - 1, -1, -1):
            for j in range(i+1, len(nums)):
                if nums[i] < nums[j]: # if less then every number in the subarray
                    DP[i] = max(DP[i], 1+DP[j])
        
        return max(DP)
```
