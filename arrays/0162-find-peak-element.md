# 0162 Find Peak Element

[Question](https://leetcode.com/problems/find-peak-element/)

<figure><img src="../.gitbook/assets/image (1) (1) (1) (2) (1).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int findPeakElement(int[] nums) {
        if(nums.length == 1){
            return 0;
        }
        
        
        int len = nums.length;
        if(nums[0] > nums[1]){
            return 0;
        }
        if(nums[len-1] > nums[len-2]){
            return len - 1;
        }
        
        
        int begin = 1;
        int end = len - 2;
        
        while(begin <= end){
            int mid = begin + (end - begin) / 2;
            if(nums[mid] > nums[mid-1]
              && nums[mid] > nums[mid+1]){
                return mid;
            }else if(nums[mid] < nums[mid-1]){
                end = mid - 1;
            }else if(nums[mid] < nums[mid+1]){
                begin = mid + 1;
            }
        }
        
        return -1;
    }
}
```
