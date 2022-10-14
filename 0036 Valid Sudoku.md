[Question](https://leetcode.com/problems/valid-sudoku/)

<img src="0036 Valid Sudoku/image-20221014111033780.png">



My solution:

```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        // validate row
        for (int r = 0; r < 9; r++) {
            boolean[] seen = new boolean[9];
            for (int c = 0; c < 9; c++) {
                if (board[r][c] == '.') {
                    continue;
                }
                if (seen[board[r][c] - '1']) {
                    return false;
                }
                seen[board[r][c] - '1'] = true;
            }
        }

        // validate col
        for (int c = 0; c < 9; c++) {
            boolean[] seen = new boolean[9];
            for (int r = 0; r < 9; r++) {
                if (board[r][c] == '.') {
                    continue;
                }
                if (seen[board[r][c] - '1']) {
                    return false;
                }
                seen[board[r][c] - '1'] = true;
            }
        }

        // validate section
        for (int r = 0; r < 9; r += 3) {
            for (int c = 0; c < 9; c += 3) {
                boolean[] seen = new boolean[9];
                for (int dr = 0; dr < 3; dr++) {
                    for (int dc = 0; dc < 3; dc++) {
                        if (board[r + dr][c + dc] == '.') {
                            continue;
                        }
                        if (seen[board[r + dr][c + dc] - '1']) {
                            return false;
                        }
                        seen[board[r + dr][c + dc] - '1'] = true;
                    }
                }
            }
        }
        return true;
    }
}
```





solution2:

```java
public boolean isValidSudoku(char[][] board) {
    Set seen = new HashSet();
    for (int i=0; i<9; ++i) {
        for (int j=0; j<9; ++j) {
            char number = board[i][j];
            if (number != '.')
                if (!seen.add(number + " in row " + i) ||
                    !seen.add(number + " in column " + j) ||
                    !seen.add(number + " in block " + i/3 + "-" + j/3))
                    return false;
        }
    }
    return true;
}
```

