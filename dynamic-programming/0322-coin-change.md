# 0322 Coin Change

[Question](https://leetcode.com/problems/coin-change/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (3) (8).png" alt=""><figcaption></figcaption></figure>

My Solution:

## JAVA

```java
class Solution {
    public int coinChange(int[] coins, int amount) {
        
        if(amount == 0){
            return 0;
        }
        Arrays.sort(coins);
        if(amount < coins[0]){
            return -1;
        }

        int[] res = new int[amount + 1];
        Arrays.fill(res, -1);
        res[0] = 0;

        for(int i = 1; i < res.length; i++){
            int min = amount + 1;
            for(int j = 0; j < coins.length; j++){
                if(i < coins[j]){
                    continue;
                }
                if(res[i-coins[j]] != -1){
                    min = Math.min(min, res[i-coins[j]]);
                }
            }
            res[i] = min == amount+1 ? -1: min+1;
        }

        return res[amount];

    }
}
```



## Python

```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        # default value: amount + 1
        # length of array: amount + 1
        dp = [amount + 1] * (amount + 1)
        dp[0] = 0

        for a in range(1, amount + 1):
            for c in coins:
                if a - c >= 0:
                    dp[a] = min(dp[a], 1 + dp[a-c])
        
        return dp[amount] if dp[amount] != amount + 1 else -1
```
