# 0020 Valid Parentheses

Question

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



My Solution:

## Python

```python
class Solution:
    def isValid(self, s: str) -> bool:
        Map = {
            ")":"(",
            "]":"[",
            "}":"{"
        }
        stack = []

        for c in s:
            if c not in Map: # not in Map mean is the left part
                stack.append(c)
                continue
            if not stack or stack[-1] != Map[c]:
                return False
            stack.pop()
        
        return not stack # if stack is not empty, means not valid
```
