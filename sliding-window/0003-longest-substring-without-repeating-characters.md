# 0003 Longest Substring Without Repeating Characters

Question

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>



My Solution:

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        charSet = set()
        l = 0
        res = 0

        for r in range(len(s)): 
            while s[r] in charSet: # contain duplicate char, move left pointer to 1 position right.
                charSet.remove(s[l]) # remove the character from the set
                l += 1
            charSet.add(s[r])
            res = max(res, r - l + 1)
        return res
```
