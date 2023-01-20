# 0739 Daily Temperatures

Question

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>



My Solution:

```python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        res = [0] * len(temperatures)
        stack = [] # stack contain pair: [temperature, index]

        for i, t in enumerate(temperatures):
            # while stack is not empty and 
            # the t is greater the last element in the stack
            while stack and t > stack[-1][0]:
                stackT, stackInd = stack.pop() #[temperature, index]
                res[stackInd] = (i - stackInd)
            stack.append([t,i])
        return res
```
