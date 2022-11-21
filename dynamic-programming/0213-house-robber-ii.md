# 0213 House Robber II

[Question](https://leetcode.com/problems/house-robber-ii/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (4) (7).png" alt=""><figcaption></figcaption></figure>

My Solution:

```java
class Solution {
    public int rob(int[] nums) {
        if(nums.length == 1){
            return nums[0];
        }

        return Math.max(maxRob(nums, 0, nums.length - 1), maxRob(nums, 1, nums.length));
    }


    private int maxRob(int[] nums, int start, int end){
        int pastRob = 0;
        int currRob = 0;
        for(int i = start; i < end; i++){
            int temp = Math.max(nums[i]+pastRob, currRob);
            pastRob = currRob;
            currRob = temp;
        }


        return currRob;
    }
}
```

