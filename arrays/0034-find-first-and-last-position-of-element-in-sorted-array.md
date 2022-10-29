# 0034 Find First and Last Position of Element in Sorted Array

[Question](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



My Solution: Binary Search

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int start = 0;
        int end = nums.length - 1;
        int fi = -1;
        
        while(start <= end){
            int mid = start + (end-start) / 2;
            if(nums[mid] == target){
                fi = mid;
                end = mid - 1;
            }else if(nums[mid] > target){
                end = mid - 1;
            }else {
                start = mid + 1;
            }
        }
        
        start = 0;
        end = nums.length - 1;
        int ei = -1;
        
        while(start <= end){
            int mid = start + (end - start) / 2;
            if(nums[mid] == target){
                ei = mid;
                start = mid + 1;
            }else if(nums[mid] > target){
                end = mid - 1;
            }else {
                start = mid + 1;
            }
        }
        
        return new int[]{fi, ei};
    }
}
```
