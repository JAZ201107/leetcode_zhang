# 0048 Rotate Image

[Question](https://leetcode.com/problems/rotate-image/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

My Solution:

```java
class Solution {
    public void rotate(int[][] matrix) {
        int n = matrix.length;
        for(int i =0; i < n; i++){
            for(int j = i; j < n; j++){
                int temp = 0;
                temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }

        for(int i = 0; i < n; i++){
            for(int j = 0; j < n/2; j++){
                int temp = 0;
                temp = matrix[i][j];
                matrix[i][j] = matrix[i][n-1-j];
                matrix[i][n-1-j] = temp;
            }
        }
    }
}
```
