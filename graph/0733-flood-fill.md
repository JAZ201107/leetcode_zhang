# 0733 Flood Fill

[Question](https://leetcode.com/problems/flood-fill/?envType=study-plan\&id=graph-i)

![](<../.gitbook/assets/image (1) (1) (2).png>)

```java
class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int newColor) {
        int start = image[sr][sc];
        if(start == newColor){
            return image;
        }
        
        dfs(sr, sc, start, newColor, image);
        
        return image;
    }
    
    
    private void dfs(int row, int col, int target, int newColor, int[][] image){
        if(row < image.length 
           && row >= 0 
           && col < image[0].length 
           && col >= 0
           && image[row][col] == target ){
            image[row][col] = newColor;
            dfs(row - 1, col, target, newColor, image);
            dfs(row, col - 1, target, newColor, image);
            dfs(row + 1, col, target, newColor, image);
            dfs(row, col + 1, target, newColor, image);
        }
    }
}
```
