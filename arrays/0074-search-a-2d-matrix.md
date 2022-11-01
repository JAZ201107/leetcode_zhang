# 0074 Search a 2D Matrix

[Question](https://leetcode.com/problems/search-a-2d-matrix/)

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

My Solution:

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int row = 0;
        int col = matrix[0].length-1;
        
        while(row < matrix.length 
             && col >=0){
            if(matrix[row][col] == target){
                return true;
            }else if(matrix[row][col] > target){
                col--;
            }else {
                row++;
            }
        }
        
        return false;
    }
}
```
