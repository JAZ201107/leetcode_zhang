# 0997 Find the Town Judge

[Question](https://leetcode.com/problems/find-the-town-judge/?envType=study-plan\&id=graph-i)

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int findJudge(int n, int[][] trust) {
        int[] Trusted = new int[n+1];
        for(int[] p: trust){
            Trusted[p[0]]--;
            Trusted[p[1]]++;
        }
        
        for(int i = 1; i < Trusted.length; i++){
            if(Trusted[i] == n-1){
                return i;
            }
        }
        
        return -1;
    }
}
```
