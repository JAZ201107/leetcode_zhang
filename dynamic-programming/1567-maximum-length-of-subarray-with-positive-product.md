# 1567 Maximum Length of Subarray With Positive Product

[Question](https://leetcode.com/problems/maximum-length-of-subarray-with-positive-product/)

![](<../.gitbook/assets/image (4) (3).png>)

My Solution:

```java
class Solution {
    public int getMaxLen(int[] nums) {
        int p = 0;
        int n = 0;
        int max = 0;
        
        for(int i: nums){
            if(i==0){
                p = 0;
                n = 0;
            }else if(i>0){
                // before is positive or negative
                // is negative: p = 0 + 1 = 1
                // is not negative eg.p = p + 1 
                p++;
                if(n > 0){ // before is negative
                    n++; // muliply positve still negative
                }
            }else if(i<0){
                // negative become postive 
                // n > 0 means before is negative
                int temp = p;
                p = n > 0? n+1: 0;
                n = temp + 1;
            }
            
            max = Math.max(p, max);
        }
        
        return max;
        
        
    }
}
```

Similar Question: [0152 Maximum Product Subarray](https://yuyang-zhang.gitbook.io/my-leetcode/dynamic-programming/0152-maximum-product-subarray)
