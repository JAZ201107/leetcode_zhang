# 0853 Car Fleet

Question

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>



My Solution

```python
class Solution:
    def carFleet(self, target: int, position: List[int], speed: List[int]) -> int:
        pair = [[p, s] for p, s in zip(position, speed)]

        stack = []
        for p, s in sorted(pair)[::-1]:
            stack.append((target - p) / s) # how many time need to get to the target
            if len(stack) >= 2 and stack[-1] <= stack[-2]:
                stack.pop()
        
        return len(stack)
```
