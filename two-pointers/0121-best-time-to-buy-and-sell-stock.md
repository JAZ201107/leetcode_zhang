# 0121 Best Time to Buy and Sell Stock

Question

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>



My Solution:

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        maxP = 0
        l, r = 0, 1

        while r < len(prices):
            if prices[l] < prices[r]:
                maxP = max(maxP, prices[r] - prices[l])
            else:
                l = r
            r += 1
        return maxP
```
