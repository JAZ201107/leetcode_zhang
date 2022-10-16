# 0200 Number of Islands

[Question](https://leetcode.com/problems/number-of-islands/)

![](<../.gitbook/assets/image (2) (1).png>)

`My Solution`

```java
class Solution {
    private int n, m;
    public int numIslands(char[][] grid) {
        n = grid.length;
        m = grid[0].length;
        
        int count = 0;
        
        if(n == 0){
            return 0;
        }
        
        for(int i = 0; i < n; i++){
            for(int j = 0; j < m; j++){
                if(grid[i][j] == '1'){
                    dfs(grid, i, j);
                    count++;
                }
            }
        }
        
        return count;
    }
    
    
    private void dfs(char[][] grid, int i, int j){
        if(i < 0 
          || j < 0 
          || i >= n
          || j >= m
          || grid[i][j] != '1'
          ){
            return;
        }
        
        
        grid[i][j] = '0';
        
        dfs(grid, i + 1, j);
        dfs(grid, i - 1, j);
        dfs(grid, i, j + 1);
        dfs(grid, i, j - 1);
    } 
}
```
