# 0139 Word Break

[Question](https://leetcode.com/problems/word-break/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (1) (1) (9).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        int len = s.length();
        Set<String> dic = new HashSet<>(wordDict);
        boolean[] p = new boolean[len+1];
        p[0] = true;

        for(int i = 1; i < len+1; i++){
            for(int j = i; j > 0; j--){
                p[i] = p[j-1] && dic.contains(s.substring(j-1, i));
                if(p[i]){
                    break;
                }
            }
        }

        return p[len];
    }
}
```
