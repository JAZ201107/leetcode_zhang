# 0198 House Robber

Question

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int rob(int[] nums) {
        int rob1 = 0, rob2 = 0;

        // [rob1, rob2, n, n+1, ...]
        for(int n : nums){
            int temp = Math.max(n + rob1, rob2);
            rob1 = rob2;
            rob2 = temp;
        }

        return rob2;
    }
}
```
