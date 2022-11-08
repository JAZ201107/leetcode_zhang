# 0079 Word Search

[Question](https://leetcode.com/problems/word-search/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public boolean exist(char[][] board, String word) {
        char[] w = word.toCharArray();
        for(int i = 0; i < board.length; i++){
            for(int j = 0; j < board[0].length; j++){
                if(helper(board,i,j,w,0)){
                    return true;
                }
            }
        }

        return false;
    }


    private boolean helper(char[][] board, int r, int c, char[] word, int index){
        if(board[r][c] == word[index]){
            char save = board[r][c];
            board[r][c] = 0;
            if((index == word.length - 1)
            || (r > 0 && helper(board, r-1, c, word, index + 1))
            || (c > 0 && helper(board, r, c-1, word, index + 1))
            || (r < board.length - 1 && helper(board, r+1, c, word, index+1))
            || (c < board[r].length - 1 && helper(board, r, c+1, word, index+1))
            ){
                return true;
            }

            board[r][c] = save;
        }

        return false;
    }
}
```
