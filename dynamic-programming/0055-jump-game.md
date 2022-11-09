# 0055 Jump Game

[Question](https://leetcode.com/problems/jump-game/description/)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public boolean canJump(int[] nums) {
        int last = nums.length - 1;
        for(int i = last; i >= 0; i--){
            if(i + nums[i] >= last){
                last = i;
            }
        }

        return last == 0;
    }
}
```
