# 0059 Spiral Matrix II

[Question](https://leetcode.com/problems/spiral-matrix-ii/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (1) (5).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int[][] generateMatrix(int n) {
        int[][] matrix = new int[n][n];

        if(n == 0){
            return matrix;
        }

        int rowStart = 0;
        int rowEnd = n-1;
        int colStart = 0;
        int colENd = n-1;
        int num = 1;

        while(rowStart <= rowEnd 
        && colStart <= colENd){
            for(int i = colStart; i <= colENd; i++){
                matrix[rowStart][i] = num++;
            }
            rowStart++;

            for(int i = rowStart; i <= rowEnd; i++){
                matrix[i][colENd] = num++;
            }
            colENd--;

            for(int i = colENd; i >= colStart; i--){
                if(rowStart <= rowEnd){
                    matrix[rowEnd][i] = num++;
                }
            }
            rowEnd--;

            for(int i = rowEnd; i>= rowStart;i--){
                if(colStart <= colENd){
                    matrix[i][colStart] = num++;
                }
            }
            colStart++;
        }

        return matrix;
    }
}
```
