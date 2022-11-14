# 0055 Jump Game

[Question](https://leetcode.com/problems/jump-game/description/)

<figure><img src="../.gitbook/assets/image (3) (6).png" alt=""><figcaption></figcaption></figure>



My Solution 1:

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



My Solution 2:

```java
class Solution {
    public boolean canJump(int[] nums) {
        int n = nums.length;

        if(n == 1){
            return true;
        }

        int[] dp = new int[n];
        dp[0] = nums[0];
        for(int i=1; i<n; i++){
            if(dp[i-1]<i){
                return false;
            }
            dp[i] = Math.max(dp[i-1], nums[i]+i); // can jump to this index.

            if(dp[i] >= n-1){
                return true; // already jump to end
            }
        }

        return dp[n-2] >= n-1;
    }
}
```

