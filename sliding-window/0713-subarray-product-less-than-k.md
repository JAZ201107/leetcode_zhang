# 0713 Subarray Product Less Than K

[Question](https://leetcode.com/problems/subarray-product-less-than-k/)

<figure><img src="../.gitbook/assets/image (8) (3).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int numSubarrayProductLessThanK(int[] nums, int k) {
        if(k <= 1){
            return 0;
        }
        
        int res = 0;
        int prod = nums[0];
        if(prod < k){
            res++;
        }
        
        int left = 0;
        int right = 1;
        
        while(right != nums.length){
            int val = nums[right];
            prod *= val;
            
            if(prod < k){
                res += right -left + 1;
            }else{
                while(prod >= k){
                    prod /= nums[left];
                    left++;
                }
                
                res += right - left + 1;
            }
            
            right++;
        }
        
        return res;
    }
}
```
