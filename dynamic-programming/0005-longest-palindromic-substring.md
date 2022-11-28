# 0005 Longest Palindromic Substring

[Question](https://leetcode.com/problems/longest-palindromic-substring/description/)

<figure><img src="../.gitbook/assets/image (2) (1) (4).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

My Solution 1: DP

```java
class Solution {
    public String longestPalindrome(String s) {
        int len = s.length();
        int start = 0;
        int end = 0;
        int max = 0;

        boolean[][] dp = new boolean[len][len];
        for(int i = 0; i < s.length(); i++){
            for(int j = 0; j <= i; j++){
                if(s.charAt(i) == s.charAt(j)
                && (i-j <= 2 || dp[j+1][i-1])){
                    dp[j][i] = true;
                }

                if(dp[j][i] && max < i-j+1){
                    max = i - j + 1;
                    start = j;
                    end = i;
                }
            }
        }

        return s.substring(start, end + 1);
    }
}
```



My Solution 2:

```java
class Solution {
    public String longestPalindrome(String s) {
        String res = "";
        int resLen = 0;

        for(int i = 0; i < s.length(); i++){
            // odd length
            int l = i, r =i;
            while( l >= 0
                && r < s.length()
                && s.charAt(l) == s.charAt(r)){
                    if(r-l+1 > resLen){
                        res = s.substring(l,r+1);
                        resLen = r - l + 1;
                    }
                    l--;
                    r++;
                }

            // even length
            l = i;
            r = i+1;
            while( l >= 0
                && r < s.length()
                && s.charAt(l) == s.charAt(r)){
                    if(r-l+1 > resLen){
                        res = s.substring(l,r+1);
                        resLen = r - l + 1;
                    }
                    l--;
                    r++;
                }
        }


        return res;
    }
}
```





## Python

My Solution:

```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        res = ""
        resLen = 0

        for i in range(len(s)):
            # odd length
            l, r = i, i
            while l >= 0 and r < len(s) and s[l] == s[r]:
                if (r-l+1) > resLen:
                    res = s[l:r+1]
                    resLen = r-l+1

                l -= 1
                r += 1

            # even length 
            l, r = i, i+1
            while l >= 0 and r < len(s) and s[l] == s[r]:
                if (r-l+1) > resLen:
                    res = s[l:r+1]
                    resLen = r-l+1

                l -= 1
                r += 1



        return res
```
