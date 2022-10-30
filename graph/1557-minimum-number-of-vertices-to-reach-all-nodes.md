# 1557 Minimum Number of Vertices to Reach All Nodes

[Question](https://leetcode.com/problems/minimum-number-of-vertices-to-reach-all-nodes/?envType=study-plan\&id=graph-i)

<figure><img src="../.gitbook/assets/image (1) (6) (1).png" alt=""><figcaption></figcaption></figure>

My Solution

```java
class Solution {
    public List<Integer> findSmallestSetOfVertices(int n, List<List<Integer>> edges) {
        List<Integer> res = new ArrayList<>();
        
        boolean[] inDegree = new boolean[n];
        
        for(List<Integer> edge: edges){
            inDegree[edge.get(1)] = true;
        }
        
        
        for(int i = 0; i< n; i++){
            if(!inDegree[i]){
                res.add(i);
            }
        }
        
        return res;
    }
}
```
