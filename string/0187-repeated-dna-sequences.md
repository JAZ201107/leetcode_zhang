# 0187 Repeated DNA Sequences

[Question](https://leetcode.com/problems/repeated-dna-sequences/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public List<String> findRepeatedDnaSequences(String s) {
        Set<String> seen = new HashSet<>();
        Set<String> repeated = new HashSet();

        for(int i = 0; i+9 < s.length(); i++){
            String temp = s.substring(i, i+10);
            if(!seen.add(temp)){
                repeated.add(temp);
            }
        }

        return new ArrayList(repeated);
    }
}
```
