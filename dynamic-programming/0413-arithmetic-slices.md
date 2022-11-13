# 0413 Arithmetic Slices

[Question](https://leetcode.com/problems/arithmetic-slices/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (1) (7).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int numberOfArithmeticSlices(int[] nums) {
        int res = 0;
        int dp[] = new int[nums.length];

        for(int i = 2; i < nums.length; i++){
            if(nums[i] - nums[i-1] == nums[i-1] - nums[i-2]){
                dp[i] = dp[i-1] + 1;
                res += dp[i];
            }
        }
        return res;
    }
}
```
