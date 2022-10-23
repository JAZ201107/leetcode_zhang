# 0695 Max Area of Island

[Question](https://leetcode.com/problems/max-area-of-island/)

![](<../.gitbook/assets/image (1) (2) (1) (1).png>)

```java
class Solution {
    private int maxArea = 0;
    public int maxAreaOfIsland(int[][] grid) {
        if(grid.length == 0
          || grid[0].length == 0){
            return 0;
        }
        
        for(int i = 0; i < grid.length; i++){
            for(int j = 0; j < grid[0].length; j++){
                int[] currArea = new int[1];
                dfs(grid, i, j, currArea);
            }
        }
        
        return maxArea;
    }
    
    private void dfs(int[][] grid, int r, int c, int[] currArea){
        if(r >= grid.length
          || c >= grid[0].length
          || r < 0
          || c < 0
          || grid[r][c] == 0){
            return;
        }
        
        grid[r][c] = 0;
        currArea[0]++;
        dfs(grid, r - 1, c, currArea);
        dfs(grid, r + 1, c, currArea);
        dfs(grid, r, c + 1, currArea);
        dfs(grid, r, c - 1, currArea);
        
        maxArea = Math.max(maxArea, currArea[0]);
    }
}
```
