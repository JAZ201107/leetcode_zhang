# 0043 Multiply Strings

[Question](https://leetcode.com/problems/multiply-strings/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (1) (2) (2).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public String multiply(String num1, String num2) {
        int num1_len = num1.length();
        int num2_len = num2.length();
        int[] pos = new int[num1_len + num2_len];

        for(int i = num1_len-1; i >= 0; i--){
            for(int j = num2_len - 1; j >= 0; j--){
                int mul = (num1.charAt(i) - '0') * (num2.charAt(j) - '0');
                int p1 = i+j;
                int p2 = i+j+1;
                int sum = mul + pos[p2];

                pos[p1] += sum / 10;
                pos[p2] = sum % 10;
            }
        }


        StringBuilder sb = new StringBuilder();
        for(int p: pos){
            if(!(sb.length()==0 && p==0)){
                sb.append(p);
            }
        }
        return sb.length() == 0 ? "0" : sb.toString();
    }
}
```
