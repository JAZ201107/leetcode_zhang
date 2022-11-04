# 0004 Median of Two Sorted Arrays

[Question](https://leetcode.com/problems/median-of-two-sorted-arrays/description/)

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int s1 = nums1.length;
        int s2 = nums2.length;

        double[] temp = new double[s1+s2];
        int i =0; // index of nums1
        int j = 0; // index of nums2
        int k = 0; // index of temp

        // merger two array
        while(i < s1
        && j < s2){
            if(nums1[i] <= nums2[j]){
                temp[k] = nums1[i];
                k++;
                i++;
            }else {
                temp[k] = nums2[j];
                j++;
                k++;
            }
        }

        if(i>=s1){
            for(int t = j; t < s2; t++){
                temp[k] = nums2[t];
                k++;
            }
        }
        if(j>=s2){
            for(int t=i;t<s1;t++){
                temp[k] = nums1[t];
                k++;
            }
        }


        double ans = 0.0;
        if(temp.length % 2 != 0){
            return  temp[temp.length/2];
        }else{
            return (temp[temp.length/2] + temp[temp.length/2-1]) / 2;
        }
    }
}
```
