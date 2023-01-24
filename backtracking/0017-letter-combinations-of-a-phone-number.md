# 0017 Letter Combinations of a Phone Number

Question

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



My Solution

```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        res = []
        digitToChar = {
            "2": "abc",
            "3": "def",
            "4": "ghi",
            "5": "jkl",
            "6": "mno",
            "7": "qprs",
            "8": "tuv",
            "9": "wxyz",
        }

        def backtrack(i, curStr):
            if len(curStr) == len(digits): # all digit have combined
                res.append(curStr)
                return

            for c in digitToChar[digits[i]]: # for every char mapped by the digit
                backtrack(i + 1, curStr + c)
            
        if digits:
            backtrack(0, "")

        return res
```
