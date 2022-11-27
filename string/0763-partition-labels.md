# 0763 Partition Labels

[Question](https://leetcode.com/problems/partition-labels/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public List<Integer> partitionLabels(String s) {
        List<Integer> list = new ArrayList<>();
        helper(s, list);
        return list;
    }

    private void helper(String s, List<Integer> list){
        if(s.length() == 0){
            return;
        }
        char first = s.charAt(0);
        int last = s.lastIndexOf(first);
        for(int i = 0; i < last; i++){
            if(s.lastIndexOf(s.charAt(i)) <= last){
                continue;
            }
            last = s.lastIndexOf(s.charAt(i));
        }
        s = s.substring(last + 1);
        list.add(last + 1);
        helper(s, list);
    }
}
```
