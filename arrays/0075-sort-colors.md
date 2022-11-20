# 0075 Sort Colors

[Question](https://leetcode.com/problems/sort-colors/description/)

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>



My Solution 1:

```java
class Solution {
    public void sortColors(int[] nums) {
        int n = nums.length;
        int[] count = new int[3];
        for(int i = 0; i < n; i++){
            count[nums[i]]++;
        }

        int i = 0;
        int n_0 = count[0];
        int n_1 = count[1];
        int n_2 = count[2];
        while(n_0 > 0){
            nums[i] = 0;
            i++;
            n_0--;
        }
        while(n_1 > 0){
            nums[i] = 1;
            i++;
            n_1--;
        }
        while(n_2 > 0){
            nums[i] = 2;
            i++;
            n_2--;
        }
    }
}
```



My Solution 2:

```java
class Solution {
    public void sortColors(int[] nums) {
        Arrays.sort(nums);
    }
}
```
