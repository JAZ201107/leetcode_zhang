# 0153 Find Minimum in Rotated Sorted Array

[Question](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int findMin(int[] nums) {
        int min = nums[0];
        int begin = 0;
        int end = nums.length - 1;
        
        while(begin <= end){
            int mid = (begin + end) / 2;
            if(mid>0 
              &&nums[mid] < nums[mid-1]){
                return nums[mid];
            }
            
            if(nums[begin] <= nums[mid]
              && nums[mid] > nums[end]){
                begin = mid + 1;
            }else{
                end = mid - 1;
            }
        }
        
        
        return nums[begin];
    }
}
```
