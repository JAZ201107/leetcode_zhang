# 0051 N-Queens

Question

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



My Solutoin:

```python
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        col = set()
        posDiag = set()
        negDiag = set()

        res = []
        board = [["."] * n for i in range(n)]

        def backtrack(r):
            if r == n: # reach the end
                copy = ["".join(row) for row in board] 
                res.append(copy)
                return 
            
            for c in range(n):
                if c in col or (r + c) in posDiag or (r - c) in negDiag: # bounding functions
                    continue # skip 
                
                col.add(c) # this column cannot put Queen
                posDiag.add(r + c) # this diagnal cannot put Queen
                negDiag.add(r - c) # this diagnal cannot put Queen
                board[r][c] = "Q"

                backtrack(r + 1) # next row

                # clean the board
                col.remove(c)
                posDiag.remove(r + c)
                negDiag.remove(r - c)
                board[r][c] = "."
            
        backtrack(0) # start from the 0 row(first row)
        return res
```
