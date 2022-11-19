# 0169 Majority Element

[Question](https://leetcode.com/problems/majority-element/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int majorityElement(int[] nums) {
        Arrays.sort(nums);
        return nums[nums.length / 2 ];
    }
}
```
