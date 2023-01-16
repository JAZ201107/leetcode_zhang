# 0746 Min Cost Climbing Stairs

Question

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int minCostClimbingStairs(int[] cost) {
        int len = cost.length;
        int last = cost[len-1];
        int sec_last = cost[len-2];
        // reverse traverse the array
        for(int i = len - 3; i >= 0; i--){
            int temp = sec_last;
            sec_last = cost[i] + Math.min(last, sec_last);
            last = temp;
        }

        return Math.min(last, sec_last);
    }
}
```
