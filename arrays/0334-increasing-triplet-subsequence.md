# 0334 Increasing Triplet Subsequence

[Question](https://leetcode.com/problems/increasing-triplet-subsequence/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public boolean increasingTriplet(int[] nums) {
        int len = nums.length;
        if(len < 3){
            return false;
        }

        int min = nums[0];
        int secondMin = Integer.MAX_VALUE;

        for(int i = 1; i < len; i++){
            if(nums[i] > secondMin){
                return true;
            }

            if(nums[i] < secondMin
            && nums[i] > min){
                secondMin = nums[i];
            }else if(nums[i] < min){
                min = nums[i];
            }
        }

        return false;
    }
}
```
