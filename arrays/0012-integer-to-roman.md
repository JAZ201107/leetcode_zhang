# 0012 Integer to Roman

[Question](https://leetcode.com/problems/integer-to-roman/)

![](<../.gitbook/assets/image (6) (1).png>)

My Solution:

```java
class Solution {
    public String intToRoman(int num) {
        int[] values = {1000,900,500,400,100,90,50,40,10,9,5,4,1};
        String[] strs = {"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};
        
        StringBuilder res = new StringBuilder();
        for(int i =0; i < values.length; i++){
            while(num >= values[i]){
                num -= values[i];
                res.append(strs[i]);
            }
        }
        
        return res.toString();
    }
    
    
}
```
