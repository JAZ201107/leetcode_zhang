# 0072 Edit Distance

[Question](https://leetcode.com/problems/edit-distance/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (3) (1) (2).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int minDistance(String word1, String word2) {
        int word1_len = word1.length();
        int word2_len = word2.length();

        int[][] cost = new int[word1_len+1][word2_len+1];
        for(int i = 0; i < word1_len+1; i++){
            cost[i][0] = i;
        }
        for(int i = 0; i < word2_len+1; i++){
            cost[0][i] = i;
        }

        for(int i = 0; i < word1_len; i++){
            for(int j = 0; j < word2_len; j++){
                if(word1.charAt(i) == word2.charAt(j)){
                    cost[i + 1][j + 1] = cost[i][j];
                }else {
                    int a = cost[i][j];
                    int b = cost[i][j+1];
                    int c = cost[i+1][j];
                    cost[i+1][j+1] = Math.min(a, Math.min(b,c));
                    cost[i+1][j+1]++;
                }
            }
        }

        return cost[word1_len][word2_len];
    }
}
```
