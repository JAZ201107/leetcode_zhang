# 0045 Jump Game II

[Question](https://leetcode.com/problems/jump-game-ii/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>





## JAVA

My Solution 1: DP

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



My Solution 2: Greedy

```java
class Solution {
    public int jump(int[] nums) {
        int res = 0;
        int l = 0, r = 0;

        while(r < nums.length - 1){
            int temp = 0;
            for(int i = l; i < r+1; i++){
                temp = Math.max(temp, i + nums[i]);
            }

            l = r + 1;
            r = temp;
            res += 1;
        }

        return res;
    }
}
```

