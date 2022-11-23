# 0202 Happy Number

[Question](https://leetcode.com/problems/happy-number/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (5) (4) (1).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public boolean isHappy(int n) {
        for(int sum = 0; n / 10 != 0 || n % 2 != 0 || n == 1; n = sum, sum = 0){
            for(int i = n; i > 0; i /= 10){
                sum += Math.pow(i%10, 2);
            }
            if(sum == 1){
                return true;
            }
        }

        return false;
    }
}
```
