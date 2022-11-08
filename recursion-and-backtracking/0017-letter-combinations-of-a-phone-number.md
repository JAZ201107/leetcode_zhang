# 0017 Letter Combinations of a Phone Number

[Question](https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public List<String> letterCombinations(String digits) {
        List<String> res = new ArrayList<String>();
        if (digits == null 
        || digits.length() == 0) {
            return res;
        }
        res.add("");
        String[] mapping = new String[] {"0", "1", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
        for (int i = 0; i < digits.length(); i++){
            List<String> newRes = new ArrayList<String>();
            char[] charArray= mapping[digits.charAt(i) - '0'].toCharArray();
            for (String str : res){
                for (char c : charArray){
                    newRes.add(new String(str + c));
                }
            }
            res = newRes;
        }
        return res;
    }
}
```
