# 1306 Jump Game III

[Question](https://leetcode.com/problems/jump-game-iii/)

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

My Solution: BFS

```java
class Solution {
    public boolean canReach(int[] arr, int start) {
        int n = arr.length;
        Queue<Integer> q = new LinkedList<>();
        q.add(start);
        
        while(!q.isEmpty()){
            int curr = q.poll();
            
            if(arr[curr] == 0){
                return true;
            }
            
            if(arr[curr] < 0){
                continue;
            }
            
            if(curr + arr[curr] < n){
                q.add(curr + arr[curr]);
            }
            if(curr - arr[curr] >=0){
                q.add(curr - arr[curr]);
            }
            
            arr[curr] = -arr[curr]; // means has been visited
        }
        
        return false;
    }
}
```



My Solution: Recursive

```java
class Solution {
    public boolean canReach(int[] arr, int start) {
        if(arr[start] == 0){
            return true;
        }
        
        if(arr[start] < 0){
            return false;
        }
        arr[start] = -arr[start];
        
        int x = start - arr[start]; // right
        if(x < arr.length && canReach(arr, x)){
            return true;
        }
        
        int y = start + arr[start]; // left
        if(y >= 0 && canReach(arr,y)){
            return true;
        }
        
        return false;
    }
}
```
