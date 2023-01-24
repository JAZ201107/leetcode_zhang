# 0131 Palindrome Partitioning

Question

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



```python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        res, part = [], []

        def backtrack(i):
            if i >= len(s): # have reach the end
                res.append(part.copy())
                return
            for j in range(i, len(s)):
                if self.isP(s, i, j): # if this substring is Palindrome
                    part.append(s[i : j + 1]) # add to part,
                    backtrack(j + 1) # check the next 
                    part.pop() # clear 
            
        backtrack(0)
        return res

    

    def isP(self, s, l ,r):
        while l < r:
            if s[l] != s[r]:
                return False
            l, r = l + 1, r - 1
        
        return True
```
