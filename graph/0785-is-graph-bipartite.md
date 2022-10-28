# 0785 Is Graph Bipartite?

[Question](https://leetcode.com/problems/is-graph-bipartite/)

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public boolean isBipartite(int[][] graph) {
        int n = graph.length;
        int[] colors = new int[n];
        
        for(int i =0; i<n;i++){
            if(colors[i] == 0
              && !validColor(graph, colors, 1, i)){
                return false;
            }
        }
        
        return true;
    }
    
    
    private boolean validColor(int[][] graph, int[] colors, int color, int node){
        if(colors[node] != 0){
            return colors[node] == color;
        }
        
        colors[node] = color;
        for(int next: graph[node]){
            if(!validColor(graph, colors, -color, next)){
                return false;
            }
        }
        
        return true;
    }
}
```
