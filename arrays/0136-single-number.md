# 0136 Single Number

[Question](https://leetcode.com/problems/single-number/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>



My Solution:&#x20;

**A ⊕ A = 0**\
**B ⊕ 0 = B**\
**A ⊕ A ⊕ B = B**

```java
class Solution {
    public int singleNumber(int[] nums) {
        for(int i = 0; i < nums.length - 1; i++){
            nums[i+1] ^= nums[i];
        }

        return nums[nums.length - 1];
    }
}
```
