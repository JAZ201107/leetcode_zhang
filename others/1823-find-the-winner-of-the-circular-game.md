# 1823 Find the Winner of the Circular Game

[Question](https://leetcode.com/problems/find-the-winner-of-the-circular-game/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

My Solution:

```python
class Solution:
    def findTheWinner(self, n: int, k: int) -> int:
        if k == 1:
            return n
        
        lst = list(range(1, n+1))
        p = n
        ptr = -1
        while p != 1:
            x = ptr + k
            ptr = x if x < p else x % p
            lst.pop(ptr)
            ptr -= 1
            p -= 1
        
        return lst[0]
```

