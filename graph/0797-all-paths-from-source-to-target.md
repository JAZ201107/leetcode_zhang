# 0797 All Paths From Source to Target

[Question](https://leetcode.com/problems/all-paths-from-source-to-target/)

![](<../.gitbook/assets/image (13) (1).png>)



My Solution: BFS

```java
class Solution {
    public List<List<Integer>> allPathsSourceTarget(int[][] graph) {
        List<List<Integer>> ans = new ArrayList<>();
        
        Queue<List<Integer>> q = new LinkedList<>();
        
        List<Integer> curr = new ArrayList<>();
        curr.add(0);
        
        q.add(curr);
        while(!q.isEmpty()){
            curr = q.poll();
            
            int v = curr.get(curr.size() - 1); // get last node
            if(v == graph.length - 1){ // is the 
                ans.add(curr);
                continue;
            }
            
            for(int i: graph[v]){ 
                List<Integer> temp = new ArrayList<>(curr);
                temp.add(i);
                q.add(temp);
            }
        }
        
        return ans;
    }
}
```



My Solution: DFS

```java
class Solution {
    public List<List<Integer>> allPathsSourceTarget(int[][] graph) {
        List<List<Integer>> ans = new ArrayList<>();
        List<Integer> path = new ArrayList<>();
        
        path.add(0);
        dfs(graph, 0, ans, path);
        
        return ans;
    }
    
    
    private void dfs(int[][] graph, int node, List<List<Integer>> ans, List<Integer> path){
        if(node == graph.length - 1){
            //is the n-1
            ans.add(new ArrayList<>(path));
            return;
        }
        
        for(int next: graph[node]){
            path.add(next);
            dfs(graph, next, ans, path);
            path.remove(path.size() - 1);
        }
    }
}
```
