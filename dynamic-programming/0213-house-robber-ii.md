# 0213 House Robber II

[Question](https://leetcode.com/problems/house-robber-ii/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (4) (7).png" alt=""><figcaption></figcaption></figure>

My Solution:

```java
class Solution {
    public int rob(int[] nums) {
        int len = nums.length;
        if(len == 1){
            return nums[0];
        }
        return Math.max(rob_range(nums, 0, len-1), rob_range(nums, 1, len));
    }

    private int rob_range(int[] nums, int begin, int end){
        int rob1 = 0, rob2 = 0;
        for(int i = begin; i < end; i++){
            int temp = Math.max(rob1 + nums[i], rob2);
            rob1 = rob2;
            rob2 = temp;
        }

        return rob2;
    }
}
```

