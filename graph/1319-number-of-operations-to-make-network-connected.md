# 1319 Number of Operations to Make Network Connected

[Question](https://leetcode.com/problems/number-of-operations-to-make-network-connected/)

![](<../.gitbook/assets/image (4) (3) (1).png>)



My Solution: Union Found

```java
class Solution {
    public int makeConnected(int n, int[][] connections) {
        int[] c= new int[n];
        int group = 0, extra = 0;
        for(int i=0; i<n; i++){
            c[i] = i;
        }
        for(int[] a: connections){
            if(union(a[0],a[1], c)){
                extra++;
            }
        }
        for(int i=0; i<n; i++){
            if(find(i,c) == i){
                group++; 
            }
        }
        
        return extra >= group-1 ? group-1:-1;
    }
    
    private boolean union(int a, int b, int[] c){
        if(find(a,c) != find(b,c)){
            c[c[a]] = c[b];
            return false;
        }else{
            return true;
        }
    }
    
    private int find(int a, int[]c){
        if(c[a] != a){
            c[a] = find(c[a],c);
        }
        return c[a];
    }
}
```
