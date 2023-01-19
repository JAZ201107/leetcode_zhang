# 0934 Shortest Bridge

[Question](https://leetcode.com/problems/shortest-bridge/)

![](<../.gitbook/assets/image (10) (1).png>)



My Solution

```java
class Solution {
    public int shortestBridge(int[][] grid) {
        boolean found = false;
        Queue<int[]> q = new LinkedList<>();
        for(int i =0; i<grid.length; i++){
            for(int j=0; j<grid[0].length; j++){
                if(grid[i][j] == 1&& !found){
                    found = true;
                    dfs(grid,i,j);
                }
                if(found && grid[i][j] == 1){
                    q.add(new int[]{i,j});
                }
            }
        }
        
        int ans = 0;
        while(!q.isEmpty()){
            int size = q.size();
            for(int c = 0; c < size; c++){
                int b[] = q.remove();
                int i = b[0];
                int j = b[1];
                if((i>0 && grid[i-1][j] == 2) 
                  || (i < grid.length-1 && grid[i+1][j] == 2)
                  || (j > 0 && grid[i][j-1] == 2)
                  || (j < grid[0].length - 1 &&grid[i][j+1] == 2)){
                    return ans;
                }
                
                if(i>0 && grid[i-1][j] == 0){
                    grid[i-1][j] = 1;
                    q.add(new int[]{i-1,j});
                }
                
                if(i < grid.length - 1&& grid[i+1][j] == 0){
                    grid[i+1][j] = 1;
                    q.add(new int[]{i+1, j});
                }
                if(j > 0 && grid[i][j-1] == 0){
                    grid[i][j-1] = 1;
                    q.add(new int[]{i, j-1});
                }
                if(j < grid[0].length - 1 && grid[i][j+1] == 0){
                    grid[i][j+1] = 1;
                    q.add(new int[]{i, j+1});
                }
            }
            ans++;
        }
        
        return 0;
    }
    
    private void dfs(int[][] grid, int i, int j){
        if (i < 0 
            || i >= grid.length 
            || j < 0 
            || j >= grid[0].length 
            || grid[i][j] == 0 
            || grid[i][j] == 2) return;
        
		grid[i][j] = 2;
        
		dfs(grid,i-1,j);
        dfs(grid,i+1,j);
        dfs(grid,i,j-1);
        dfs(grid,i,j+1);
    }
}
```
