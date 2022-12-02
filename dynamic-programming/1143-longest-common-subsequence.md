# 1143 Longest Common Subsequence

[Question](https://leetcode.com/problems/longest-common-subsequence/description/?envType=study-plan\&id=algorithm-ii)

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>



My Solution:

<figure><img src="../.gitbook/assets/image (2) (3).png" alt=""><figcaption></figcaption></figure>

```java
class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        char[] text1_arr = text1.toCharArray();
        char[] text2_arr = text2.toCharArray();

        int text1_len = text1.length();
        int text2_len = text2.length();

        int[][] arr = new int[text1_len+1][text2_len+1];

        for(int i = 0; i < text1_len + 1; i++){
            arr[i][0] = 0;
        }

        for(int i = 0; i < text2_len + 1; i++){
            arr[0][i] = 0;
        }


        for(int i = 1; i < text1_len+1; i++){
            for(int j = 1; j < text2_len+1; j++){
                if(text1_arr[i-1] == text2_arr[j-1]){
                    arr[i][j] = arr[i-1][j-1] + 1;
                }else{
                    arr[i][j] = Math.max(arr[i-1][j], arr[i][j-1]);
                }
            }
        }

        return arr[text1_len][text2_len];
    }
}
```



Relative Question:

* 0583 Delete Operation for Two Strings
