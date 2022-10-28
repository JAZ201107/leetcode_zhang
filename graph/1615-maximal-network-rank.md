# 1615 Maximal Network Rank

[Question](https://leetcode.com/problems/maximal-network-rank/)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

My Solution:

```java
class Solution {
    public int maximalNetworkRank(int n, int[][] roads) {
        int[] numRoadConnectedCity = new int[100+1];
        
        boolean[][] r = new boolean[n][n];
        
        for(int[] cities: roads){
            // increment the count of numbers of connected city
            numRoadConnectedCity[cities[0]]++;
            numRoadConnectedCity[cities[1]]++;
            
            
            // mark road exist between two cities
            r[cities[0]][cities[1]] = true;
            r[cities[1]][cities[0]] = true;
        }
        
        
        int maxRank = 0;
        for(int i = 0; i < n-1; i++){
            for(int j = i+1; j < n; j++){
                int rank = numRoadConnectedCity[i] + numRoadConnectedCity[j];
                if(r[i][j]){
                    rank--;  // two connected road
                }
                maxRank = Math.max(maxRank, rank);
            }
        }
        
        return maxRank;
    }
}
```



