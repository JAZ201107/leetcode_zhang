# 0071 Simplify Path

<figure><img src="../.gitbook/assets/image (1) (11).png" alt=""><figcaption></figcaption></figure>



My Solution:

```python
class Solution:
    def simplifyPath(self, path: str) -> str:
        stack = []
        cur = ""
        for c in path + "/":
            if c =="/":
                if cur == "..":
                    if stack: stack.pop()
                elif cur != "" and cur != ".":
                    stack.append(cur)
                cur = ""
            else:
                cur += c
        
        return "/" + "/".join(stack)
```
