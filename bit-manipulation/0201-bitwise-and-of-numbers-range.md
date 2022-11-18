# 0201 Bitwise AND of Numbers Range

[Question](https://leetcode.com/problems/bitwise-and-of-numbers-range/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>





My Solution:

```java
class Solution {
    public int rangeBitwiseAnd(int left, int right) {
        int i = 0;
        for(; left != right; i++){
            left >>= 1;
            right >>= 1;
        }

        return right << i;
    }
}
```

