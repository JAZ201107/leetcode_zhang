# 0169 Majority Element

[Question](https://leetcode.com/problems/majority-element/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (1) (9).png" alt=""><figcaption></figcaption></figure>



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



My Solution 3: [**Boyer-Moore voting**](https://www.geeksforgeeks.org/boyer-moore-majority-voting-algorithm/)****

```java
class Solution {
    public int majorityElement(int[] nums) {
        int count = 0;
        int candidate = 0;
        for(int i: nums){
            if(count == 0){
                candidate = i;
            }
            if(i != candidate){
                count--;
            }else{
                count++;
            }
        }

        return candidate;
    }
}
```



My Solution 4:

```java
class Solution {
    public int majorityElement(int[] nums) {
        int[] bit = new int[32];
        for(int num: nums){
            for(int i = 0; i < 32; i++){
                if((num >> (31 - i) & 1) == 1){
                    bit[i]++;
                }
            }
        }
        int res = 0;
        for(int i = 0; i < 32; i++){
            bit[i] = bit[i] > nums.length/2 ? 1:0;
            res += bit[i] * (1<<(31-i));
        }
        return res;
    }
}
```
