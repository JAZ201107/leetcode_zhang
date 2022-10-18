# 1905 Count Sub Islands

[Question](https://leetcode.com/problems/count-sub-islands/)

![](<../.gitbook/assets/image (2) (1).png>)



```java
class Solution {
    int ans = 0;
    public int countSubIslands(int[][] grid1, int[][] grid2) {
        int count = 0;
        for(int i =0; i < grid2.length; i++){
            for(int j=0; j < grid2[0].length; j++ ){
                if(grid2[i][j] == 1){
                    ans = 1;
                    helper(grid1, grid2, i, j);
                    count += ans;
                }
            }
        }
        
        return count;
    }
    
    public void helper(int[][] grid1, int[][] grid2, int i, int j){
        if(i < 0 
           || j < 0 
           || i >= grid1.length 
           || j >= grid1[0].length 
           || grid2[i][j] == 0) {
            return;
        }
		// if the corresponding cell in grid1 is water, then we just make ans = 0.
        if(grid1[i][j] == 0) ans = 0;
        grid2[i][j] = 0;
        helper(grid1, grid2, i-1, j);
        helper(grid1, grid2, i+1, j);
        helper(grid1, grid2, i, j+1);
        helper(grid1, grid2, i, j-1);
    }
}
```
