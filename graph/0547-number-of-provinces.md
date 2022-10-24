# 0547 Number of Provinces

[Question](https://leetcode.com/problems/number-of-provinces/)

![](<../.gitbook/assets/image (1) (3).png>)



My Solution: DFS

```java
class Solution {
    public int findCircleNum(int[][] isConnected) {
        int n = isConnected.length;
        
        boolean[] visited = new boolean[n];
        int count = 0;
        
        for(int i =0; i<n; i++){
            if(!visited[i]){
                count++;
                dfs(isConnected, i, visited);
            }
        }
        
        return count;
    }
    
    
    private void dfs(int[][] isConnected, int i, boolean[] visited){
        for(int j =0; j < isConnected[i].length; j++){
            if(!visited[j] && isConnected[i][j] != 0 ){
                visited[j] = true;
                dfs(isConnected, j, visited);
            }
        }
    }
}
```



My Solution: BFS

```java
class Solution {
    public int findCircleNum(int[][] isConnected) {
        int n = isConnected.length;
        int count = 0;
        
        boolean[] visited = new boolean[n];
        Queue<Integer> q = new LinkedList<>();
        
        for(int i=0; i < n; i++){
            if(!visited[i]){
                q.offer(i);
                count++;
            }
            
            while(!q.isEmpty()){
                int curr = q.poll();
                visited[curr] = true;
                for(int j = 0;j < n; j++){
                    if(j != curr
                      && isConnected[curr][j] == 1
                      && !visited[j]){
                        q.offer(j);
                    }
                }
            }
        }
        return count;
    }
}
```

