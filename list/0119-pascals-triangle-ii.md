# 0119 Pascal's Triangle II

[Question](https://leetcode.com/problems/pascals-triangle-ii/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> res = new ArrayList<>();
        for(int i = 0; i < rowIndex+1; i++){
            res.add(1);
            for(int j = i-1; j > 0; j--){
                res.set(j, res.get(j-1) + res.get(j));
            }
        }

        return res;
    }
}
```



My Solution 2: DP

```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> res = new ArrayList<>();
        int[][] dp = new int[rowIndex+1][rowIndex+1];
        dp[0][0] = 1;
        for(int i =0; i <= rowIndex; i++){
            for(int j = 0; j <= i; j++){
                if(j == 0){
                    dp[i][j] = 1;
                    if(i == rowIndex){
                        res.add(dp[i][j]);
                    }
                }else {
                    dp[i][j] = dp[i-1][j] + dp[i-1][j-1];
                    if(i==rowIndex){
                        res.add(dp[i][j]);
                    }
                }
            }
        }

        return res;
    }
}
```
