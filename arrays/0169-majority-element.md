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



My Solution 2:

```java
class Solution {
    public int majorityElement(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>();
        int res = 0;
        for(int i : nums){
            map.put(i, map.getOrDefault(i, 0) + 1);
            if(map.get(i) > nums.length / 2){
                res = i;
                return res;
            }
        }

        return res;
    }
}
```
