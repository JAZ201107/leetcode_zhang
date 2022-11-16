# 0343 Integer Break

[Question](https://leetcode.com/problems/integer-break/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

My Solution:

```java
class Solution {
    public int integerBreak(int n) {
        int[] res = new int[n+1];
        res[0] = 0;
        res[1] = 1;

        for(int i = 2; i <= 6 && i <= n; i++){
            res[i] = (int)i/2 * (i - (int)i/2);
        }

        for(int i = 7; i <= n; i++){
            res[i] = Math.max(res[i-2] * 2, res[i-3] * 3);
        }

        return res[n];
    }
}
```
