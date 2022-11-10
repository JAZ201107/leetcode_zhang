# 0045 Jump Game II

[Question](https://leetcode.com/problems/jump-game-ii/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

My Solution:

```java
class Solution {
    public int jump(int[] nums) {
        int steps = 0;
        int end = 0;
        int max = 0;
        for(int i = 0; i < nums.length - 1; i++){
            max = Math.max(max, i + nums[i]);
            if(i==end){
                steps++;
                end = max;
            }
        }
        return steps;
    }
}
```

