# 0415 Add Strings

[Question](https://leetcode.com/problems/add-strings/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public String addStrings(String num1, String num2) {
        int num1_len = num1.length() - 1;
        int num2_len = num2.length() - 1;

        StringBuilder sb = new StringBuilder();
        int carry = 0;

        while(num1_len >= 0
        || num2_len >= 0
        || carry > 0){
            int n1 = 0;
            int n2 = 0;
            if(num1_len >= 0){
                n1 = num1.charAt(num1_len) - '0';
                num1_len--;
            }
            if(num2_len >= 0){
                n2 = num2.charAt(num2_len) - '0';
                num2_len--;
            }

            int num = (n1+n2+carry) % 10;
            carry = (n1+n2+carry) >= 10? 1:0;
            sb.append(num);
        }

        return sb.reverse().toString();
    }
}
```
