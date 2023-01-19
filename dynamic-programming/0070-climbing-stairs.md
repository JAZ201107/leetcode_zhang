# 0070 Climbing Stairs

Question:

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int climbStairs(int n) {
        int one = 1, two = 1;
        for(int i = 0; i < n-1; i++){
            int temp = one;
            one = one + two;
            two = temp;
        }
        return one;
    }
}
```
