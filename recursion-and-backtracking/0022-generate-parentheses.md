# 0022 Generate Parentheses

[Question](https://leetcode.com/problems/generate-parentheses/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (1) (3).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> list = new ArrayList<String>();
        helper(list, "", 0, 0, n);
        return list;
    }

    private void helper(List<String> list, String str, int open, int close, int max){
        if(str.length() == max * 2){
            list.add(str);
            return;
        }

        if(open < max){
            helper(list, str + "(", open + 1, close, max);
        }
        if(close < open){
            helper(list, str + ")", open, close + 1, max);
        }
    }
}
```
