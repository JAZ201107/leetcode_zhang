# 0209 Minimum Size Subarray Sum

[Question](https://leetcode.com/problems/minimum-size-subarray-sum/)

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int left = 0;
        int right = 0;
        int sum = 0;
        int min = Integer.MAX_VALUE;
        
        while(right < nums.length){
            sum += nums[right];
            if(sum < target){
                right++;
            }else{
                min = Math.min(min, right - left + 1);
                sum -= nums[left];
                sum -= nums[right];
                left++;
            }
        }
        
        
        return min == Integer.MAX_VALUE ? 0: min;
    }
}
```
