[Question](https://leetcode.com/problems/longest-consecutive-sequence/)

<img src="0128 Longest Consecutive Sequence/image-20221014113736148.png">



My Solution:

```java
class Solution {
    public int longestConsecutive(int[] nums) {
        if (nums.length == 0 || nums.length == 1){
            return nums.length;
        }
        Arrays.sort(nums);
        int max = -1;
        int cur = 1;
        for(int i=0; i < nums.length-1; i++){
            if(nums[i+1]  == nums[i] + 1){
                cur += 1;
            }else if(nums[i+1]  == nums[i]){
                continue;
            }else{
                if(cur > max)
                    max = cur;
                cur = 1;
            }
        }
        
        
        return max > cur? max: cur;
    }
}
```

