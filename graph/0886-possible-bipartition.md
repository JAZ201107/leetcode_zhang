# 0886 Possible Bipartition

[Question](https://leetcode.com/problems/possible-bipartition/)

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public boolean possibleBipartition(int n, int[][] dislikes) {
        List<Integer>[] graph = new List[n+1];
        for(int i = 1; i<=n; i++){
            graph[i] = new ArrayList<>();
        }
        
        for(int[] dislike: dislikes){
            graph[dislike[0]].add(dislike[1]);
            graph[dislike[1]].add(dislike[0]);
        }
        
        Integer[] colors = new Integer[n+1];
        for(int i = 1; i<=n;i++){
            if(colors[i] == null 
              && !dfs(graph, colors, i ,1)){
                return false;
            }
        }
        
        return true;
    }
    
    
    private boolean dfs(List<Integer>[] graph, Integer[] colors, int currNode, int currColor){
        colors[currNode] = currColor;
        
        for(Integer a: graph[currNode]){
            if(colors[a] == null){
                if(!dfs(graph, colors, a, currColor * -1)){
                    return false;
                }
            }else if(colors[a] == currColor){
                return false;
            }
        }
        
        
        return true;
    }
}
```
