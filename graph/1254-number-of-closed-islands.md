# 1254 Number of Closed Islands

[Question](https://leetcode.com/problems/number-of-closed-islands/)

![](<../.gitbook/assets/image (4) (1) (1) (1).png>)

```java
class Solution {
    private boolean isClosed = true;
    public int closedIsland(int[][] grid) {
        if(grid.length == 0
          || grid[0].length ==0){
            return 0;
        }
        
        int count = 0;
        for(int i = 0; i < grid.length; i++){
            for(int j = 0; j < grid[0].length; j++){
                
                if(grid[i][j] == 0){
                    dfs(grid, i, j);
                    if(isClosed){
                        count++;
                    }
                    isClosed = true;
                }
                
            }
        }
        
        return count;
    }
    
    private void dfs(int[][] grid, int i, int j){
        if(   i<0 
           || j<0 
           || i>=grid.length 
           || j>=grid[0].length 
           || grid[i][j]==1){
            return;
        }
        
        if(
            (   i==0 
             || j==0 
             || i==grid.length-1 
             || j==grid[0].length-1
            ) 
            && grid[i][j]==0){
            isClosed = false;
        }
        
        grid[i][j]=1;
    
        dfs(grid,i-1,j);
        dfs(grid,i+1,j);
        dfs(grid,i,j-1);
        dfs(grid,i,j+1);
    }
}
```
