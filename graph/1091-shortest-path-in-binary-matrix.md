# 1091 Shortest Path in Binary Matrix

[Question](https://leetcode.com/problems/shortest-path-in-binary-matrix/)

![](<../.gitbook/assets/image (7) (1).png>)

My Solution: BFS Search

```java
class Solution {
    public int shortestPathBinaryMatrix(int[][] grid) {
        int ans = 0;
        
        int row = grid.length;
        int col = grid[0].length;
        
        if(grid[0][0] == 1 || grid[row-1][col-1] == 1){
            return -1;
        }
        
        // 8 directions
        int[][] dirs = {
            {-1,-1},
            {-1, 0},
            {-1, 1},
            {0 ,-1},
            {0 , 1},
            {1 ,-1},
            {1 , 0},
            {1 , 1}
        };
        
        
        boolean[][] visited = new boolean[row][col];
        
        Queue<int[]> queue = new LinkedList<>();
        queue.offer(new int[]{0,0});
        visited[0][0] = true;
        
        while(!queue.isEmpty()){
            int size = queue.size();
            ans++;
            
            for(int i=0; i<size; i++){
                int[] curPos = queue.poll();
                if(curPos[0] == row - 1 && curPos[1] == col -1){
                    return ans;
                }
                
                for(int[] dir: dirs){
                    int nextX = curPos[0] + dir[0];
                    int nextY = curPos[1] + dir[1];
                    
                    if(nextX < 0
                      || nextX >= row
                      || nextY < 0
                      || nextY >= col
                      || visited[nextX][nextY]
                      || grid[nextX][nextY] == 1){
                        continue;
                    }
                    
                    visited[nextX][nextY] = true;
                    queue.offer(new int[]{nextX, nextY});
                }
            }
        }
        
        
        return -1;
    }
}
```



My Solution2: A\* Search

```java
class Solution {
    public int shortestPathBinaryMatrix(int[][] grid) {
        int N = grid.length;
        
        if (grid[0][0] != 0 || grid[N - 1][N - 1] != 0) {
            return -1;
        }

        int directions[][] = {{-1,0},{1,0},{0,1},{0,-1},{1,1},{1,-1},{-1,1},{-1,-1}};
        
        Queue<Attempt> attempts = new PriorityQueue<>();
        attempts.add(new Attempt(0, 0, 1));
        while (!attempts.isEmpty()) {
           Attempt attempt = attempts.poll();
            
           if (attempt.row == N - 1 && attempt.column == N - 1) {
               return attempt.step;
           } 
            
           for (int[] direction : directions) {
               int row = attempt.row + direction[0];
               int column = attempt.column + direction[1];
               
               if (row >= 0 && row < N && column >= 0 && column < N && grid[row][column] == 0) {
                   attempts.add(new Attempt(row, column, attempt.step + 1));
                   grid[row][column] = -1; 
                }  
           } 
        }
        
        return -1;
    }
    
    class Attempt implements Comparable<Attempt> {
        int row;
        int column;
        int step;
        
        public Attempt (int row, int column, int step) {
            this.row = row;
            this.column = column;
            this.step = step;
        }
        
        @Override
        public int compareTo(Attempt other) {
            if (this.step == other.step) {
                return other.row + other.column - this.row - this.column;
            }
            
            return this.step - other.step;
        }
    }
}
```

