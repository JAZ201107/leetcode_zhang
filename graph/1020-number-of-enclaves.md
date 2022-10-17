# 1020 Number of Enclaves

[Question](https://leetcode.com/problems/number-of-enclaves/)

![](<../.gitbook/assets/image (4).png>)



```java
class Solution {
    public int numEnclaves(int[][] grid) {
        int rows, cols;
        
        rows = grid.length;
        cols = grid[0].length;
        
        for(int i=0; i < rows; i++){
            for(int j=0; j < cols; j++){
                if(
                (i==0 || j==0 || i==rows-1 || j == cols-1)
                    && (grid[i][j] == 1)
                ){
                    helper(grid, i, j);
                }
            }
        }
        
        int count = 0;
        for(int i=0; i < rows; i++){
            for(int j=0; j < cols; j++){
                if(grid[i][j] == 1){
                    count++;
                }
            }
        }
        
        return count;
    }
    
    private void helper(int[][] grid, int i, int j){
        if(i <0
          || i>=grid.length
          || j<0
          || j>=grid[0].length
          || grid[i][j] ==0){
            return;
        }
        
        grid[i][j] = 0;
        
        helper(grid, i+1, j);
        helper(grid, i-1, j);
        helper(grid, i, j+1);
        helper(grid, i, j-1);
    }
}
```
