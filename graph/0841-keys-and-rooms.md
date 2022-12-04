# 0841 Keys and Rooms

[Question](https://leetcode.com/problems/keys-and-rooms/submissions/)

![](<../.gitbook/assets/image (12) (1).png>)

My Solution: DFS

```java
class Solution {
    public boolean canVisitAllRooms(List<List<Integer>> rooms) {
        boolean visited[] = new boolean[rooms.size()]; // may contain circle or self-lopp
        dfs(rooms.get(0), 0, rooms, visited);
        
        for(int i = 0; i<visited.length; i++){
            if(!visited[i]){
                return false;
            }
        }
        
        return true;
        
    }
    
    
    private void dfs(List<Integer> keysInRoom, int room, List<List<Integer>> rooms, boolean[] visited){
        visited[room] = true; // mark as visited
        for(int i: keysInRoom){
            if(!visited[i]){
                dfs(rooms.get(i), i, rooms, visited);
            }
        }
    }
}
```



My Solution: BFS

```java
class Solution {
    public boolean canVisitAllRooms(List<List<Integer>> rooms) {
        Set<Integer> visited = new HashSet<>();
        Queue<Integer> q = new LinkedList<>();
        
        q.add(0);
        
        while(!q.isEmpty()){
            // remove curr room
            int curr = q.remove();
            
            if(visited.contains(curr)){
                continue; // has been visited
            }
            
            visited.add(curr); // mark as visited
            
            // bread search
            for(int i: rooms.get(curr)){
                if(!visited.contains(i)){
                    q.add(i);
                }
            }
        }
        
        return visited.size() == rooms.size();
    }
}
```

