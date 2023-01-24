# 1466 Reorder Routes to Make All Paths Lead to the City Zero

[Question](https://leetcode.com/problems/reorder-routes-to-make-all-paths-lead-to-the-city-zero/)

<figure><img src="../.gitbook/assets/image (1) (2) (3) (2).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int minReorder(int n, int[][] connections) {
        List<List<Integer>> adj = new ArrayList<>();
        for(int i=0; i<n; i++){
            adj.add(new LinkedList<>());
        }
        
        for(int[] c: connections){
            adj.get(c[0]).add(c[1]);
            adj.get(c[1]).add(-c[0]);
        }
        
        boolean[] visited = new boolean[n];
        return dfs(adj, visited, 0);
    }
    
    
    private int dfs(List<List<Integer>> adj, boolean[] visited, int v){
        int reOrderCount = 0;
        visited[v]  = true;
        List<Integer> children = adj.get(v);
        for(Integer child: children){
            if(!visited[Math.abs(child)]){
                reOrderCount += dfs(adj, visited, Math.abs(child)) + (child > 0 ? 1:0);
            }
        }
        
        return reOrderCount;
    }
}
```
