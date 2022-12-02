# 1249 Minimum Remove to Make Valid Parentheses

[Question](https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

My Solution:

```python
class Solution:
    def minRemoveToMakeValid(self, s: str) -> str:
        stack = []
        s_len = len(s)
        s_list = list(s)

        for i in range(s_len):
            if s_list[i] == "(":
                stack.append(i)
            elif s_list[i] == ")":
                if stack:
                    stack.pop()
                else:
                    s_list[i] = ""  #remove ")"
        
        for j in stack:  #remove "("
            s_list[j] = ""
        
        return "".join(s_list)
        
```
